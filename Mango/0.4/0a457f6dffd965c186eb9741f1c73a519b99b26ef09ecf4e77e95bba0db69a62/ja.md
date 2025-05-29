```
send_and_handle_answer(
response_handler::Function,
agent::AgentInterface,
content::Any,
agent_address::Address;
calling_object::Any=nothing,
kwargs...)
```

応答を処理するためのトラッキングされたメッセージを送信するための便利なメソッドです。

必要な response_handler を使用してトラッキングされたメッセージを送信し、次の構文を使用できるようにします。

```
send_and_handle_answer(...) do agent, message, meta
	# 応答を処理する
end
```
