```
MultiHeadAttention(dims; nheads=1, dense_kwargs=(; use_bias=False()),
                   attention_dropout_probability=0.0f0)
```

Transformerアーキテクチャで使用されるマルチヘッドドット積アテンション層 [vaswani2017attention](@citep)。

## 引数

  * `dims`: 入力、内部テンソル、および出力の埋め込み次元。最も一般的な場合、次のように与えられます。         a) `(q_in_dim, k_in_dim, v_in_dim) => (qk_dim, v_dim) => out_dim`。         より単純な形も取ることができます。         b) `dims::Int`；         c) `in_dim::Int => (qk_dim, v_dim) => out_dim`；         d) `in_dim::Int => qkv_dim => out_dim`。

## キーワード引数

  * `nheads`: ヘッドの数。
  * `attention_dropout_probability`: アテンションスコアのドロップアウト確率。
  * `dense_kwargs`: Dense層のためのキーワード引数。デフォルトは `use_bias=false`。

## フォワードパスシグネチャ

```
(m::MultiHeadAttention)(qkv, ps, st::NamedTuple)
(m::MultiHeadAttention)((q, kv), ps, st::NamedTuple)
(m::MultiHeadAttention)((q, k, v, [mask = nothing]), ps, st::NamedTuple)
```

## 入力

  * `qkv`: クエリ、キー、および値のための単一の入力テンソル。これは自己注意に対応します。
  * `(q, kv)`: クエリとキー-バリューのための2つの入力テンソルのタプル。
  * `(q, k, v)`: クエリ、キー、および値のための3つの入力テンソルのタプル。
  * `mask`: アテンションスコアに適用するオプションのマスク。これはアテンションスコアの形状 `(kv_len, q_len, nheads, batch_size)` にブロードキャスト可能でなければなりません。

クエリテンソル `q` は形状 `(q_in_dim, q_len, batch_size)` を持つことが期待され、キーのテンソル `k` は形状 `(k_in_dim, kv_len, batch_size)` を持つことが期待され、値のテンソル `v` は形状 `(v_in_dim, kv_len, batch_size)` を持つことが期待されます。

## 戻り値

  * 2つの要素からなるタプル。最初の要素は形状 `(out_dim, q_len, batch_size)` の出力テンソルであり、2番目の要素は形状 `(q_len, kv_len, nheads, batch_size)` のアテンションスコアです。
  * 層の状態のNamedTuple。

# 拡張ヘルプ

## 例

```jldoctest
julia> m = MultiHeadAttention(64; nheads=8);

julia> ps, st = Lux.setup(Random.default_rng(), m);

julia> q = randn(Float32, 64, 10, 32);

julia> k = randn(Float32, 64, 20, 32);

julia> v = randn(Float32, 64, 20, 32);

julia> (y, α), st_new = m((q, k, v), ps, st);

julia> size(y)
(64, 10, 32)

julia> size(α)
(20, 10, 8, 32)

julia> (y, α), st_new = m(q, ps, st);  # 自己注意

julia> size(y)
(64, 10, 32)

julia> size(α)
(10, 10, 8, 32)
```
