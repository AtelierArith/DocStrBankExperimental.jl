```
onehot_batch(tokenizer::AbstractSequenceTokenizer, batch::AbstractVector{UInt32})
```

トークン化されたシーケンスのバッチをワンホット表現に変換します。

この関数は、トークンインデックスのベクターを受け取り、提供されたトークナイザーのアルファベットを使用してワンホットエンコードされた表現に変換します。

# 引数

  * `tokenizer::AbstractSequenceTokenizer`: シーケンスに使用されるトークナイザー。その長さがワンホットエンコーディングの次元のサイズを決定します。
  * `batch::AbstractVector{UInt32}`: ワンホット表現に変換されるトークンインデックスのベクター。

# 戻り値

  * `OneHotArray`: 入力バッチのワンホットエンコードされた表現。結果の配列は (length(tokenizer), length(batch)) の次元を持ちます。

# 例

```julia
alphabet = ['a', 'b', 'c']
tokenizer = SequenceTokenizer(alphabet, 'x')
tokenized_sequence = [2, 3, 1, 4]  # ['a', 'b', 'x', 'c'] に対応
onehot = onehot_batch(tokenizer, tokenized_sequence)
println(size(onehot))  # 出力: (4, 4)
println(onehot[:, 1])  # 出力: [0, 1, 0, 0]
```

# 注意

この関数は、入力バッチ内のすべてのインデックスがトークナイザーのアルファベットに対して有効であると仮定しています。有効範囲外のインデックスは、エラーや予期しない動作を引き起こす可能性があります。

# 参照

  * [`SequenceTokenizer`](@ref): 入力バッチを作成するために使用されるトークナイザー構造体。
  * [`onecold_batch`](@ref): ワンホット表現をトークンインデックスに戻す逆操作。
