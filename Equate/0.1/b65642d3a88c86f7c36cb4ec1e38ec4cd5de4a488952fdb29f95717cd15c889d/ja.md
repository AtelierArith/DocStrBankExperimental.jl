```
presmoothing(F::FreqTab, @LogLinearFormula(df::Int64))
```

元の頻度データの最初のCモーメントを保持し、`LogLinearFormula(C)`を`fml`に渡して、`SmoothedFreqTab`としての平滑化された頻度テーブルと`glm`フィッティングオブジェクトを返します。Cは自由度です。

# 例

```julia
julia> tab = freqtab(expandtable(ACTmath.scale, ACTmath.xcount));
julia> presmoothing(tab, Equate.fml₄)
Equate.SmoothedFreqTab(40×5 DataFrame
│ Row │ scale   │ freq     │ cumfreq  │ prob        │ cumprob     │
│     │ Float64 │ Float64? │ Float64? │ Float64     │ Float64     │
├─────┼─────────┼──────────┼──────────┼─────────────┼─────────────┤
│ 1   │ 1.0     │ 0.864929 │ 0.864929 │ 0.000199799 │ 0.000199799 │
│ 2   │ 2.0     │ 2.47529  │ 3.34022  │ 0.000571794 │ 0.000771592 │
⋮
│ 38  │ 38.0    │ 31.9351  │ 4291.07  │ 0.00737703  │ 0.991238    │
│ 39  │ 39.0    │ 22.7842  │ 4313.85  │ 0.00526315  │ 0.996501    │
│ 40  │ 40.0    │ 15.1484  │ 4329.0   │ 0.00349928  │ 1.0         │, [1, 2, 3, 3, 3, 4, 4, 4, 4, 4  …  40, 40, 40, 40, 40, 40, 40, 40, 40, 40], 1.0, StatsModels.TableRegressionModel{GLM.GeneralizedLinearModel{GLM.GlmResp{Array{Float64,1},Distributions.Poisson{Float64},GLM.LogLink},GLM.DensePredChol{Float64,LinearAlgebra.Cholesky{Float64,Array{Float64,2}}}},Array{Float64,2}}

freq ~ 1 + scale + :(scale ^ 2) + :(scale ^ 3) + :(scale ^ 4)

係数:
─────────────────────────────────────────────────────────────────────────────────
                   Coef.   Std. Error       z  Pr(>|z|)    Lower 95%    Upper 95%
─────────────────────────────────────────────────────────────────────────────────
(Intercept)  -1.35982     0.310243      -4.38    <1e-4   -1.96789     -0.751757
scale         1.30127     0.0728808     17.85    <1e-70   1.15843      1.44412
scale ^ 2    -0.089081    0.00589528   -15.11    <1e-50  -0.100636    -0.0775265
scale ^ 3     0.00254824  0.000195003   13.07    <1e-38   0.00216604   0.00293044
scale ^ 4    -2.67698e-5  2.25114e-6   -11.89    <1e-31  -3.1182e-5   -2.23576e-5
─────────────────────────────────────────────────────────────────────────────────)

```
