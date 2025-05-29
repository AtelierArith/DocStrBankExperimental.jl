Open a Websocket client to the v2/marketdata endpoint

https://docs.gemini.com/websocket-api/#market-data-version-2

# Arguments:

  * `sandbox::Bool`: Sandbox request
  * `channel::Channel{Dict}`: channel to pass data
  * `names::Vector`: data feed name subscriptions (l2, candles_1m,...)
  * `symbols::Vector`: symbol subscriptions (BTCUSD,...)
