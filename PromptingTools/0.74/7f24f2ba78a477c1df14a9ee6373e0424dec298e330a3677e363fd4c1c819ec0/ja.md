```
ai"user_prompt"[model_alias] -> AIMessage
```

`ai""`文字マクロは、内部で`aigenerate`を使用して、与えられたプロンプトに対するAIの応答を生成します。

提供されたメッセージに返信したり、会話を続けたい場合は、`ai!""`も参照してください。

## 引数

  * `user_prompt` (String): AIモデルへの入力プロンプト。
  * `model_alias` (オプション、任意): AIモデルのモデルエイリアスを提供します（`MODEL_ALIASES`を参照）。

## 戻り値

入力プロンプトに対応する`AIMessage`。

## 例

```julia
result = ai"Hello, how are you?"
# AIMessage("Hello! I'm an AI assistant, so I don't have feelings, but I'm here to help you. How can I assist you today?")
```

いくつかの変数や追加のコンテキストを補間したい場合は、単に文字列補間を使用します：

```julia
a=1
result = ai"What is `$a+$a`?"
# AIMessage("The sum of `1+1` is `2`.")
```

異なるモデル、例えばGPT-4を使用したい場合は、フラグとしてそのエイリアスを提供できます：

```julia
result = ai"What is `1.23 * 100 + 1`?"gpt4t
# AIMessage("The answer is 124.")
```
