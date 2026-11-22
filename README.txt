CRT DERIV ANALYST - LIVE DATA PROTOTYPE V1

This is an Android-friendly Progressive Web App prototype.
It connects to Deriv's public WebSocket market-data endpoint:
wss://api.derivws.com/trading/v1/options/ws/public

It requests active_symbols, subscribes to ticks and requests historical candles
for 300, 900, 3600 and 14400 second intervals. It requires no Deriv password or token.

IMPORTANT LIMITATIONS:
- This is a live-data integration prototype, not a completed production trading system.
- The app's market-category grouping is heuristic and needs validation against Deriv's
  actual active_symbols metadata; unknown instruments remain available under All markets.
- The preliminary CRT logic is intentionally conservative and is not yet the complete
  agreed ruleset. It currently evaluates the previous completed 1H candle, 4H candle
  direction, 15M candle direction and 5M wick sweep/reclaim plus candle-body displacement.
- It does not yet implement robust swing-based MSS/CHoCH, FVG lifecycle, equal highs/lows,
  sessions, signal persistence, backtesting or background push notifications.
- Browser notifications only work while the page/browser can run. Real background push
  requires HTTPS deployment and a push subscription backend.
- Public Deriv market data is not guaranteed to match every Deriv MT5 server/feed exactly.
  Compare candle OHLC values against the user's MT5 account before treating feeds as equivalent.
- It never places trades and does not ask for account credentials.

ANDROID:
Host the folder on an HTTPS static host. Open the URL in Chrome on Android, then Chrome menu
> Install app / Add to Home screen. Service workers and PWA installation require HTTPS
(or localhost). Opening index.html directly from a file manager will not provide full PWA
functionality.
