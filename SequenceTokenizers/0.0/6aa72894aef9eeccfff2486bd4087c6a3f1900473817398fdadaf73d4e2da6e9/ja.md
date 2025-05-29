```
onecold_batch(tokenizer::AbstractSequenceTokenizer, onehot_batch::OneHotArray)
```

ワンホット表現をトークン化されたシーケンスに戻します。

# 引数

  * `tokenizer::AbstractSequenceTokenizer`: シーケンスに使用されるトークナイザー
  * `onehot_batch::OneHotArray`: シーケンスのワンホットエンコーディングを表すOneHotArray

# 戻り値

トークン化されたシーケンスを表すインデックスの行列

# 例

```julia
alphabet = ['a', 'b', 'c']
tokenizer = SequenceTokenizer(alphabet, 'x')
sequences = [['a', 'b'], ['c', 'a', 'b']]
tokenized = tokenizer(sequences)
onehot = onehot_batch(tokenizer, tokenized)
recovered = onecold_batch(tokenizer, onehot)
# 回復した結果はバッチ処理されているため、パディングが残ります
println(recovered == ['a' 'c'; 'b' 'a'; 'x' 'b']) # 出力: true
```
