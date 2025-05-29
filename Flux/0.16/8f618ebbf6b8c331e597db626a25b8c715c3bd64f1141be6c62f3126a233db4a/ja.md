```
MultiHeadAttention(dims; [nheads, bias, init, dropout_prob])
```

Transformerアーキテクチャで使用されるマルチヘッドドット積アテンション層 [1]。

変換された入力シーケンスとアテンションスコアを返します。

[1] Vaswani et al. "Attention is all you need." Advances in Neural Information Processing Systems. 2017.

# 引数

  * `dims`: 入力、内部テンソル、および出力の埋め込み次元。最も一般的な場合、次のように与えられます。          a) `(q_in_dim, k_in_dim, v_in_dim) => (qk_dim, v_dim) => out_dim`。         より単純な形も取ることができます。         b) `dims::Int`；         c) `in_dim::Int => (qk_dim, v_dim) => out_dim`；         d) `in_dim::Int => qkv_dim => out_dim`。
  * `nheads`: ヘッドの数。デフォルトは `8`。
  * `init`: Dense層の重み初期化子。デフォルトは `glorot_uniform`。
  * `bias` : ポイントワイズQKVO密変換がバイアスを使用するかどうか。デフォルトは `false`。
  * `dropout_prob`: アテンションスコアのドロップアウト確率。デフォルトは `0.0`。

# フォワード

```
(mha::MultiHeadAttention)(q_in, k_in, v_in, [bias]; [mask])
```

フォワードパスの引数は次のとおりです。

  * `q_in`: サイズ `(q_in_dim, q_len, batch_size)` の入力クエリ配列。
  * `k_in`: サイズ `(k_in_dim, kv_len, batch_size)` の入力キー配列。
  * `v_in`: サイズ `(v_in_dim, kv_len, batch_size)` の入力値配列。
  * `bias`: サイズ `(kv_len, q_len, nheads, batch_size)` にブロードキャスト可能なバイアス配列。         ソフトマックスの前にアテンションスコアに加算されます。         デフォルトは `nothing`。
  * `mask`: サイズ `(kv_len, q_len, nheads, batch_size)` にブロードキャスト可能な入力配列。          マスクはソフトマックスの直前にアテンションスコアに適用されます。          因果マスクを作成するには [`NNlib.make_causal_mask`](@ref) を参照してください。          デフォルトは `nothing`。

代替呼び出しシグネチャは `mha(q_in)` で、`mha(q_in, q_in, q_in)`（自己注意）と同等です。また、`mha(q_in, k_in)` は `mha(q_in, k_in, k_in)`（キーと値が同じ）と同等です。

[`NNlib.dot_product_attention`](@ref) も参照してください。

# 例

```julia
mha = MultiHeadAttention(64, nheads = 8)
q = rand(Float32, (64, 10, 32))
k = rand(Float32, (64, 20, 32))
v = rand(Float32, (64, 20, 32))
y, α = mha(q, k, v) 
# [y] = [64, 10, 32]
# [α] = [20, 10, 8, 32]

mha = MultiHeadAttention(64 => 1024 => 1024, nheads = 8)
y, α = mha(q) # 自己注意
# [y] = [1024, 10, 32]
# [α] = [10, 10, 8, 32]
```
