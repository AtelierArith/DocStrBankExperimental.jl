```
create_padding_mask(lengths::Vector{Int}, max_len::Int)
```

バッチ化された異なる長さのシーケンスのためのパディングマスクを作成します。これにより、パディングされた位置（各シーケンスの実際の長さを超える位置）がマスクされ、注意に参加しないようになります。

# 引数

  * `lengths::Vector{Int}`: バッチ内の各シーケンスの実際の長さ
  * `max_len::Int`: 最大シーケンス長（パディングされた長さ）

# 戻り値

  * 形状が (batch*size, max*len, 1) の 3D ブール配列で、True はパディングされた位置を示します

# 例

```
# 長さ 2 と 3 の 2 つのシーケンスが長さ 4 にパディングされた場合:
julia> mask = create_padding_mask([2, 3], 4)[:,:,1]
2×4 Matrix{Bool}:
 0  0  1  1  # 最初のシーケンス: 長さ 2、位置 3-4 はパディング
 0  0  0  1  # 2 番目のシーケンス: 長さ 3、位置 4 はパディング
```

# 因果マスクとの使用

パディングマスクと因果マスクは、バッチ化された自己回帰タスクのためにしばしば組み合わされます：

```
seq_len = 5
batch_lengths = [3, 4]

# 両方のマスクを作成
causal = create_causal_mask(seq_len)                # 形状: (5, 5, 1)
padding = create_padding_mask(batch_lengths, seq_len) # 形状: (2, 5, 1)

# マスクを組み合わせ、将来のトークンまたはパディングトークンへの注意を防ぎます
combined = causal .| padding

# final_mask は以下を防ぎます:
# 1. 将来のトークンへの注意（因果マスクから）
# 2. パディングトークンへの注意（パディングマスクから）
```
