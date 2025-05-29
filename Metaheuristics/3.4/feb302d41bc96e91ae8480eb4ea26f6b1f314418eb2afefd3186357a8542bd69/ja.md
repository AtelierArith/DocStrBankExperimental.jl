```
DE(;
    N  = 0,
    F  = 1.0,
    CR = 0.5,
    strategy = :rand1,
    information = Information(),
    options = Options()
)

差分進化 (DE) アルゴリズムのパラメータ: ステップサイズ `F`、`CR` は二項交差を制御し、`N` は集団サイズです。パラメータ `strategy` は変異演算子に関連しています（`:rand1`、`:rand2`、`:best1`、`:best2`、`:randToBest1`）。

# 例

```

jldoctest julia> f(x) = sum(x.^2) f (generic function with 1 method)

julia> optimize(f, [-1 -1 -1; 1 1 1.0], DE()) +=========== RESULT ==========+   iteration: 1000     minimum: 0   minimizer: [0.0, 0.0, 0.0]     f calls: 30000  total time: 0.0437 s +============================+

julia> optimize(f, [-1 -1 -1; 1 1 1.0], DE(N=50, F=1.5, CR=0.8)) +=========== RESULT ==========+   iteration: 600     minimum: 8.68798e-25   minimizer: [3.2777877981303293e-13, 3.7650459509488005e-13, -7.871487597385812e-13]     f calls: 30000  total time: 0.0319 s +============================+ ```
