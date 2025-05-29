```
dot_product_attention(query, key, value, [bias]; [fdrop, mask, nheads])
```

トランスフォーマーアーキテクチャで使用されるマルチヘッドドット積アテンション。

入力配列は、最初の2次元が特徴量の数とシーケンスの長さである必要があり、その後は任意の数のバッチ次元またはなしである必要があります。

アテンション出力配列のサイズは `(v_dim, q_len, batch_size...)` で、アテンションスコアのサイズは `(kv_len, q_len, nheads, batch_size...)` です。

アテンションスコアのみが必要な場合は、[`dot_product_attention_scores`](@ref) も参照してください。

# 引数

  * `query`: サイズ `(qk_dim, q_len, batch_size...)` のクエリ配列。
  * `key`: サイズ `(qk_dim, kv_len, batch_size...)` のキー配列。
  * `value`: サイズ `(v_dim, kv_len, batch_size...)` の値配列。
  * `bias`: `nothing` またはサイズ `(kv_len, q_len, nheads, batch_size)` にブロードキャスト可能な配列。ソフトマックスを適用する前にアテンションスコアに加算されます。デフォルトは `nothing`。
  * `fdrop`: ソフトマックスの直後にアテンションスコアに適用されるドロップアウト関数またはレイヤー。デフォルトは `identity`（ドロップアウトなし）。
  * `mask`: `nothing` またはサイズ `(kv_len, q_len, nheads, batch_size)` にブロードキャスト可能なブール配列。マスクはソフトマックスの直前にアテンションスコアに適用されます。因果マスクを作成するには、[`make_causal_mask`](@ref) を参照してください。デフォルトは `nothing`。
  * `nheads`: 入力配列を分割するヘッドの数。デフォルトは `1`。

# 例

```julia
q, k, v = rand(10, 20, 2), rand(10, 30, 2), rand(20, 30, 2)
y, α = dot_product_attention(q, k, v)
```
