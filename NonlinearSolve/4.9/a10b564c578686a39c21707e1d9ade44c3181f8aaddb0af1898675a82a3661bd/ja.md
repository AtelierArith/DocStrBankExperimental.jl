```
LeastSquaresOptimJL(alg = :lm; linsolve = nothing, autodiff::Symbol = :central)
```

`NonlinearLeastSquaresProblem`を解くための[LeastSquaresOptim.jl](https://github.com/matthieugomez/LeastSquaresOptim.jl)のラッパーです。

### 引数

  * `alg`: 使用するアルゴリズム。`:lm`または`:dogleg`を指定できます。

### キーワード引数

  * `linsolve`: 使用する線形ソルバー。`:qr`、`:cholesky`、または`:lsmr`を指定できます。`nothing`の場合、`LeastSquaresOptim.jl`はヤコビ行列の構造に基づいて最適な線形ソルバーを選択します。
  * `autodiff`: 自動微分 / 有限差分。`:central`または`:forward`を指定できます。

!!! note
    このアルゴリズムは`LeastSquaresOptim.jl`がインストールされ、ロードされている場合にのみ利用可能です。

