Websocketクライアントをv2/marketdataエンドポイントに開く

https://docs.gemini.com/websocket-api/#market-data-version-2

# 引数:

  * `sandbox::Bool`: サンドボックスリクエスト
  * `channel::Channel{Dict}`: データを渡すチャネル
  * `names::Vector`: データフィード名のサブスクリプション (l2, candles_1m,...)
  * `symbols::Vector`: シンボルのサブスクリプション (BTCUSD,...)
