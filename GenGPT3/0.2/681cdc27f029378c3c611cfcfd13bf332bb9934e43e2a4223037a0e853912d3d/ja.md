```
GPT3Trace
```

[`GPT3GenerativeFunction`](@ref)によって生成されたトレースです。このトレースには、言語モデルによって生成された完了出力を示す正確に1つの選択アドレス`output`があります。戻り値も完了出力です。

`Base.getindex(trace::GPT3Trace, addr)`は、`addr`に対して以下の値をサポートします：

  * `:prompt`: 言語モデルに引数として提供されたプロンプト。
  * `:output`: 言語モデルによって生成された出力完了。
  * `:tokens`: 停止シーケンスを含む出力トークンのベクター。
  * `:token_logprobs`: 各トークンの対数確率。
  * `:score`: 出力を生成するための総対数確率。
