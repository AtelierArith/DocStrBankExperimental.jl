```
(tokenizer::SequenceTokenizer{T})(batch::AbstractVector{<:AbstractString}) where T
```

文字列シーケンスのバッチをトークン化し、短いシーケンスには未知のトークンでパディングします。

# 引数

  * `tokenizer::SequenceTokenizer{T}`: 使用するトークナイザー
  * `batch::AbstractVector{<:AbstractString}`: トークン化される文字列シーケンスのベクター

# 戻り値

各列がトークン化されパディングされたシーケンスを表すインデックスの行列

# 例

```julia
tokenizer = SequenceTokenizer(['A','T','G','C'], 'N')
sequences = ["ATG", "ATGCGC"]
result = tokenizer(sequences)
```
