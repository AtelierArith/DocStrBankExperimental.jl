```
send_and_handle_answer(
response_handler::Function,
agent::AgentInterface,
content::Any,
agent_address::Address;
calling_object::Any=nothing,
kwargs...)
```

Convenience method for sending tracked messages with response handler to the answer.

Sends a tracked message with a required response_handler to enable to use the syntax

```
send_and_handle_answer(...) do agent, message, meta
	# handle the answer
end
```
