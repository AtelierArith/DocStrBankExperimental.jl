```
send_tracked_message(
agent::AgentInterface,
content::Any,
agent_address::Address;
response_handler::Function=(agent, message, meta) -> nothing,
calling_object::Any=nothing,
kwargs...,
)

`content`を持つメッセージを`agent_address`で表されるエージェントに送信します。この関数は、ダイアログの識別を可能にする生成されたtracking_idをアドレスに設定します。

`response_handler`を定義することが可能で、これに関数を割り当てることができ、このメッセージ呼び出しに対する回答を処理します。応答するエージェントは、理想的には[`reply_to`](@ref)を使用して自動的にこれを達成するために、同じtracking idを応答に使用する必要があることに注意してください。

このメソッドは常にsender_idを設定します。さらに、メッセージの内部メタデータを埋めるために、他のキーワード引数を定義することができます。
```
