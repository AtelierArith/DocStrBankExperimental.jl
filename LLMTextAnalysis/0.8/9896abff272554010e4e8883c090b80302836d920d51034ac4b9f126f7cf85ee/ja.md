```
cross_validate_accuracy(X::AbstractMatrix{<:Number},
                        y::AbstractVector{<:Integer};
                        verbose::Bool = true,
                        k::Int = 4,
                        lambda::Real = 1e-5) -> Float64
```

データセット `(X, y)` に対してロジスティック回帰を使用して k-分割交差検証を実行し、平均分類精度を返します。

# 引数

  * `X::AbstractMatrix`: 特徴行列（観測 x 特徴）。
  * `y::AbstractVector{<:Integer}`: ターゲットベクトル（+-1）
  * `verbose::Bool`（オプション）: `true` の場合、各フォールドの精度を出力します。デフォルトは `true` です。
  * `k::Int`（オプション）: 交差検証のフォールド数。デフォルトは 4 です。
  * `lambda::Real`（オプション）: ロジスティック回帰の正則化パラメータ。デフォルトは 1e-5 です。

# 戻り値

  * `Float64`: すべてのフォールドにわたる平均分類精度。

# 例

```julia
acc = cross_validate_accuracy(Xt, y; k = 4, lambda = 1e-2)
```
