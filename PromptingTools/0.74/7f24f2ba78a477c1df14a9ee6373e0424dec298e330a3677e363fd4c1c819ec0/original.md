```
ai"user_prompt"[model_alias] -> AIMessage
```

The `ai""` string macro generates an AI response to a given prompt by using `aigenerate` under the hood.

See also `ai!""` if you want to reply to the provided message / continue the conversation.

## Arguments

  * `user_prompt` (String): The input prompt for the AI model.
  * `model_alias` (optional, any): Provide model alias of the AI model (see `MODEL_ALIASES`).

## Returns

`AIMessage` corresponding to the input prompt.

## Example

```julia
result = ai"Hello, how are you?"
# AIMessage("Hello! I'm an AI assistant, so I don't have feelings, but I'm here to help you. How can I assist you today?")
```

If you want to interpolate some variables or additional context, simply use string interpolation:

```julia
a=1
result = ai"What is `$a+$a`?"
# AIMessage("The sum of `1+1` is `2`.")
```

If you want to use a different model, eg, GPT-4, you can provide its alias as a flag:

```julia
result = ai"What is `1.23 * 100 + 1`?"gpt4t
# AIMessage("The answer is 124.")
```
