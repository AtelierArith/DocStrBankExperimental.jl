```
PSO(;
    N  = 0,
    C1 = 2.0,
    C2 = 2.0,
    ω  = 0.8,
    information = Information(),
    options = Options()
)

粒子群最適化（PSO）アルゴリズムのパラメータ：学習率 `C1` と `C2`、`N` は集団サイズ、`ω` は慣性重みを制御します。

# 例

```

jldoctest julia> f(x) = sum(x.^2) f (generic function with 1 method)

julia> optimize(f, [-1 -1 -1; 1 1 1.0], PSO()) +=========== RESULT ==========+   iteration: 1000     minimum: 1.40522e-49   minimizer: [3.0325415595139883e-25, 1.9862212295897505e-25, 9.543772256546461e-26]     f calls: 30000  total time: 0.1558 s +============================+

julia> optimize(f, [-1 -1 -1; 1 1 1.0], PSO(N = 100, C1=1.5, C2=1.5, ω = 0.7)) +=========== RESULT ==========+   iteration: 300     minimum: 2.46164e-39   minimizer: [-3.055334698085433e-20, -8.666986835846171e-21, -3.8118413472544027e-20]     f calls: 30000  total time: 0.1365 s +============================+ ```
