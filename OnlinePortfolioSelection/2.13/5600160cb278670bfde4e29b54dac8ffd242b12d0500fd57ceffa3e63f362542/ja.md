```
OPSAlgorithm{T<:AbstractFloat}
```

アルゴリズムを実行した結果を含むオブジェクトです。

# フィールド

  * `n_asset::Int`: ポートフォリオ内の資産の数。
  * `b::Matrix{T}`: 作成されたポートフォリオの重み。
  * `alg::String`: アルゴリズムの名前。
