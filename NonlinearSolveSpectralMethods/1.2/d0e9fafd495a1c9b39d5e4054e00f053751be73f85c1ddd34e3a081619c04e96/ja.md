```
DFSane(;
    sigma_min = 1 // 10^10, sigma_max = 1e10, sigma_1 = 1, M::Int = 10,
    gamma = 1 // 10^4, tau_min = 1 // 10, tau_max = 1 // 2, n_exp::Int = 2,
    max_inner_iterations::Int = 100, eta_strategy = (fn_1, n, x_n, f_n) -> fn_1 / n^2
)
```

大規模非線形方程式系を解くための低オーバーヘッドでアロケーションフリーのdf-saneメソッドの実装。すべてのパラメータとアルゴリズムに関する詳細情報については、[la2006spectral](@citet)を参照してください。

### キーワード引数

  * `sigma_min`: アルゴリズムのステップサイズに関連するスペクトル係数 `σ` の最小値。デフォルトは `1e-10`。
  * `sigma_max`: アルゴリズムのステップサイズに関連するスペクトル係数 `σₙ` の最大値。デフォルトは `1e10`。

他のキーワード引数については、[`RobustNonMonotoneLineSearch`](@ref)を参照してください。
