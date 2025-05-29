Kucoin.subscribe(ws*client, topic[, id[, is*private*channel[, return*response]]]) -> nothing

Send a subscription message to the server.  See Kucoin official [docs](https://docs.kucoin.com/#subscribe) for more details.

# Arguments

  * `ws_client::WebSocketClient`: web socket client
  * `topic::String`: the topic you want to subscribe to
  * `id::String`: [Optional] is unique string to mark the request which is same as id property

of ack.

  * `is_private_channel::Bool`: [Optional] for some specific topics (e.g. `/market/level2`),

`is_private_channel` is available. If the `is_private_channel` is set to true, the user will  only receive messages related to himself on the topic.

  * `return_response::Bool`: [Optional] if is set as true, kucoin will return the

acknowledgment message after successful subscription.
