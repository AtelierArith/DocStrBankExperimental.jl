```
(rope::RoPE)(x) -> AbstractArray
```

入力配列 `x` に対して回転位置埋め込みを適用します。形状は `(head_size, seq_len, batch * num_heads)` です。

# 引数

  * `x`: 最初の次元が `rope.head_size` と一致し、2 番目の次元が最大キャッシュシーケンス長を超えない必要がある入力配列。

関連情報: [`RoPE`](@ref)
