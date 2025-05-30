```
send_tracked_message(
agent::AgentInterface,
content::Any,
agent_address::Address;
response_handler::Function=(agent, message, meta) -> nothing,
calling_object::Any=nothing,
kwargs...,
)

内容 `content` を `agent_address` で表されるエージェントに送信します。この関数は、ダイアログを識別するための生成された tracking_id をアドレスに設定します。

このメッセージ呼び出しに対する回答を処理する関数を割り当てることができる `response_handler` を定義することが可能です。応答するエージェントは、理想的には [`reply_to`](@ref) を使用して自動的にこれを達成するために、同じ tracking id を応答に使用する必要があることに注意してください。

このメソッドは常に sender_id を設定します。さらに、メッセージの内部メタデータを埋めるために、他のキーワード引数を定義することができます。
```
