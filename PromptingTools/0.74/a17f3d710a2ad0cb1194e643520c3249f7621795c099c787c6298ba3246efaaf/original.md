```
aai"user_prompt"[model_alias] -> AIMessage
```

Asynchronous version of `@ai_str` macro, which will log the result once it's ready.

See also `aai!""` if you want an asynchronous reply to the provided message / continue the conversation.    

# Example

Send asynchronous request to GPT-4, so we don't have to wait for the response: Very practical with slow models, so you can keep working in the meantime.

```julia m = aai"Say Hi!"gpt4; 

# ...with some delay...

# [ Info: Tokens: 29 @ Cost: 0.0011 in 2.7 seconds

# [ Info: AIMessage> Hello! How can I assist you today?
