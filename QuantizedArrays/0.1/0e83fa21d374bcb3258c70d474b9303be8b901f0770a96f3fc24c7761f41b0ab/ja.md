```
build_codebooks(X, k, m, U [;method=DEFAULT_METHOD, distance=DEFAULT_DISTANCE, kwargs])
```

入力行列 `X` に対して、指定されたアルゴリズム `method` と距離 `distance` を使用して、各 `k` プロトタイプの `m` コードブックを生成します。特定のコードブックアルゴリズムのキーワード引数も指定できます。

# 引数

  * `X::AbstractMatrix{T}` 型 `T` の入力行列
  * `k::Int` プロトタイプ/コードブックの数
  * `m::Int` コードブックの数
  * `U::Type{<:Unsigned}` コードブックコードの型

# キーワード引数

  * `method::Symbol` コードブック生成に使用されるアルゴリズム; 可能な値は `:sample` (デフォルト)、`:pq` は古典的な k-means クラスタリングコードブック、`:opq` は「直交」k-means クラスタリングコードブックです。
  * `distance::PreMetric` コードブック生成メソッドおよびデータエンコーディングに使用される距離
  * `kwargs...` `maxiter::Int` のような他のコードブック生成アルゴリズム特有のキーワード引数。
