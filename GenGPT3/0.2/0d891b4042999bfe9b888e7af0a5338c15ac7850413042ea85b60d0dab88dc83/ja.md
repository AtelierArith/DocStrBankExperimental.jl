```
MultiGPT3Trace
```

[`MultiGPT3GenerativeFunction`](@ref)によって生成されたトレース。実質的には、[`GPT3Trace`](@ref)サブトレースのベクトルを表します。

`Base.getindex(trace::MultiGPT3Trace, addr)`は、`addr`に対して以下の値をサポートします：

  * `:prompts`: 言語モデルに提供されたプロンプト。
  * `:outputs`: 各プロンプトに対して生成された出力。
  * `:tokens`: 停止シーケンスを含む出力トークンのベクトルのベクトル。
  * `:token_logprobs`: トークンの対数確率のベクトルのベクトル。
  * `:output_scores`: 各出力の対数確率。
  * `:score`: すべての出力を生成するための総対数確率。

さらに、`addr`は`i => subaddr`の形式を取ることができ、ここで`i`は整数であり、`i`-thサブトレースの`:prompt`、`:output`、`:tokens`、`:token_logprobs`、または`:score`にアクセスするために使用されます。
