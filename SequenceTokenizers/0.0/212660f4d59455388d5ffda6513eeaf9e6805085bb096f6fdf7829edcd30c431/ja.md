```
(tokenizer::SequenceTokenizer{T})(input::AbstractString) where T
```

SequenceTokenizerを使用して文字列入力をトークン化します。

このメソッドは、入力文字列を型Tのトークンのベクターに効率的に変換し、各要素にトークナイザーを適用します。

# 引数

  * `tokenizer::SequenceTokenizer{T}`: 使用するトークナイザー
  * `input::AbstractString`: トークン化される入力文字列

# 戻り値

入力文字列の文字に対応するトークンインデックスのVector{UInt32}

# パフォーマンスノート

  * このメソッドは、文字列を型Tのベクターに変換するために`collect(T, input)`を使用します
  * 特定のコンテキストでのパフォーマンス向上のために`@inline`としてマークされています

# 例

```julia
alphabet = ['a', 'b', 'c']
tokenizer = SequenceTokenizer(alphabet, 'x')
result = tokenizer("abcx")
println(result)  # 出力: [2, 3, 4, 1]
```
