```
onehot_batch(tokenizer::SequenceTokenizer, batch::AbstractMatrix{UInt32})
```

トークン化されたシーケンスのバッチをワンホット表現に変換します。

# 引数

  * `tokenizer::SequenceTokenizer`: シーケンスに使用されるトークナイザー
  * `batch::AbstractMatrix{UInt32}`: トークン化されたシーケンスの行列

# 戻り値

入力バッチのワンホットエンコーディングを表す OneHotArray

# 例

```julia
alphabet = ['a', 'b', 'c']
tokenizer = SequenceTokenizer(alphabet, 'x')
sequences = [["a", "b"], ["c", "a", "b"]]
tokenized = tokenizer(sequences)
onehot = onehot_batch(tokenizer, tokenized)
println(size(onehot))  # 出力: (4, 3, 2)
```
