```
(tokenizer::SequenceTokenizer{T})(x::AbstractArray) where T
```

シンボルの配列をトークン化します。

# 引数

  * `x::AbstractArray`: トークン化されるシンボルの配列

# 戻り値

入力シンボルに対応するインデックスの配列

# 例

```julia
alphabet = ['a', 'b', 'c']
tokenizer = SequenceTokenizer(alphabet, 'x')
println(tokenizer(['a', 'b', 'z', 'c']))  # 出力: [2, 3, 1, 4]
```
