```
ccf(X, y; starting_lambdas = nothing)
```

クリップされた凸関数のための符号付き勾配降下法を、与えられた回帰設定で実行します。

# 引数

  * `X::AbstractMatrix{Float64}`: 線形モデルの設計行列。
  * `y::AbstractVector{Float64}`: 線形モデルの応答ベクトル。
  * `starting_lambdas::AbstractVector{Float64}`: 符号付き勾配降下法で使用される重みパラメータの初期値。
  * `alpha::Float64`: 点が外れ値としてラベル付けされる損失。指定されていない場合、p*mean(residuals.^2)として選択されます。ここで、residualsはOLS残差です。
  * `p::Float64`: OLS残差の二乗が平均二乗OLS残差のp倍を超える点は外れ値と見なされます。
  * `max_iter::Int64`: 符号付き勾配降下法を実行する最大反復回数。
  * `beta::Float64`: ステップサイズパラメータ。
  * `tol::Float64`: 収束が宣言される許容範囲。

# 出力

  * `["betas"]`: ロバスト回帰係数
  * `[""outliers"]`: 外れ値のインデックスの配列
  * `[""lambdas"]`: 各反復で推定されたラムダ係数
  * `[""residuals"]`: 回帰残差。

# 参考文献

Barratt, S., Angeris, G. & Boyd, S. Minimizing a sum of clipped convex functions. Optim Lett 14, 2443–2459 (2020). https://doi.org/10.1007/s11590-020-01565-4
