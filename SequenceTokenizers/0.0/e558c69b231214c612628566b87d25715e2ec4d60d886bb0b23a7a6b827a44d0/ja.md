```
(tokenizer::SequenceTokenizer)(idx::Integer)
```

インデックスを対応するトークンに戻します。

# 引数

  * `idx::Integer`: トークンに戻すためのインデックス

# 戻り値

トークナイザーのアルファベットにおける指定されたインデックスに対応するトークン

# 例

```julia
alphabet = ['a', 'b', 'c']
tokenizer = SequenceTokenizer(alphabet, 'x')
println(tokenizer(2))  # 出力: 'a'
println(tokenizer(1))  # 出力: 'x' (不明なトークン)
```
