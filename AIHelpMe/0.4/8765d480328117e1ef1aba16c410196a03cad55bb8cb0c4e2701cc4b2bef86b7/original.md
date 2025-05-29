```
aihelp"user_question"[model_alias] -> AIMessage
```

The `aihelp""` string macro generates an AI response to a given user question by using `aihelp` under the hood. It will automatically try to provide the most relevant bits of the documentation (from the index) to the LLM to answer the question.

See also `aihelp!""` if you want to reply to the provided message / continue the conversation.

## Arguments

  * `user_question` (String): The question to be answered by the AI model.
  * `model_alias` (optional, any): Provide model alias of the AI model (see `MODEL_ALIASES`).

## Returns

`AIMessage` corresponding to the input prompt.

## Example

```julia
result = aihelp"Hello, how are you?"
# AIMessage("Hello! I'm an AI assistant, so I don't have feelings, but I'm here to help you. How can I assist you today?")
```

If you want to interpolate some variables or additional context, simply use string interpolation:

```julia
a=1
result = aihelp"What is `$a+$a`?"
# AIMessage("The sum of `1+1` is `2`.")
```

If you want to use a different model, eg, GPT-3.5 Turbo, you can provide its alias as a flag:

```julia
result = aihelp"What is `1.23 * 100 + 1`?"gpt3t
# AIMessage("The answer is 124.")
```
