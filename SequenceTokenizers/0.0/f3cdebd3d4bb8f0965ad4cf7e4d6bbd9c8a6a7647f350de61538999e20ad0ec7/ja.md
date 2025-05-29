```
(tokenizer::SequenceTokenizer{T})(batch::AbstractVector{<:AbstractVector{T}}) where T
```

シーケンスのバッチをトークン化し、短いシーケンスには未知のトークンでパディングします。

# 引数

  * `batch::AbstractVector{<:AbstractVector{T}}`: トークン化されるシーケンスのベクトル

# 戻り値

各列がトークン化されパディングされたシーケンスを表すインデックスの行列

# 例

```julia
alphabet = ['a', 'b', 'c']
tokenizer = SequenceTokenizer(alphabet, 'x')
sequences = [['a', 'b'], ['c', 'a', 'b']]
println(tokenizer(sequences))
# 出力:
# [2 4
#  3 2
#  1 3]
```
