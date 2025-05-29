```
presmoothing(F::EG, degree::Int64)
```

生のスコアヒストグラムに対してログ線形モデルをフィッティングするための自由度のさまざまな度合いを調べます。

# 例

```julia
julia> tab = freqtab(expandtable(ACTmath.scale, ACTmath.xcount))
Equate.FreqTab(40×5 DataFrame
│ Row │ scale   │ freq  │ cumfreq │ prob       │ cumprob  │
│     │ Float64 │ Int64 │ Int64   │ Float64    │ Float64  │
├─────┼─────────┼───────┼─────────┼────────────┼──────────┤
│ 1   │ 1.0     │ 1     │ 1       │ 0.000231   │ 0.000231 │
│ 2   │ 2.0     │ 1     │ 2       │ 0.000231   │ 0.000462 │
⋮
│ 38  │ 38.0    │ 38    │ 4291    │ 0.00877801 │ 0.991222 │
│ 39  │ 39.0    │ 23    │ 4314    │ 0.00531301 │ 0.996535 │
│ 40  │ 40.0    │ 15    │ 4329    │ 0.003465   │ 1.0      │, [1, 2, 3, 3, 3, 4, 4, 4, 4, 4  …  40, 40, 40, 40, 40, 40, 40, 40, 40, 40], 1.0)

julia> fit = presmoothing(tab, 10)
Fitting dof = 1 model.
Fitting dof = 2 model.
Fitting dof = 3 model.
Fitting dof = 4 model.
Fitting dof = 5 model.
Fitting dof = 6 model.
Fitting dof = 7 model.
Fitting dof = 8 model.
Fitting dof = 9 model.
Fitting dof = 10 model.
10×7 DataFrame. Omitted printing of 1 columns
│ Row │ degree │ aic     │ aicc    │ bic     │ loglik   │ deviance │
│     │ Int64  │ Float64 │ Float64 │ Float64 │ Float64  │ Float64  │
├─────┼────────┼─────────┼─────────┼─────────┼──────────┼──────────┤
│ 1   │ 1      │ 2235.18 │ 2235.5  │ 2238.56 │ -1115.59 │ 1988.28  │
│ 2   │ 2      │ 661.558 │ 662.225 │ 666.625 │ -327.779 │ 412.654  │
⋮
│ 8   │ 8      │ 290.675 │ 296.675 │ 305.875 │ -136.338 │ 29.7704  │
│ 9   │ 9      │ 292.573 │ 300.159 │ 309.462 │ -136.286 │ 29.6683  │
│ 10  │ 10     │ 294.051 │ 303.48  │ 312.629 │ -136.026 │ 29.1466  │

```
