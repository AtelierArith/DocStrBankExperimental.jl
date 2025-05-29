```
VarEffect(formula, covtype::T, coding) where T <: AbstractCovarianceType

VarEffect(formula, covtype::T; coding = nothing) where T <: AbstractCovarianceType

VarEffect(formula; coding = nothing)
```

ランダム/繰り返し効果。

  * `formula` は @covstr(ex) マクロから。
  * `covtype` - 共分散タイプ (SI, DIAG, CS, CSH, AR, ARH, ARMA, TOEP, TOEPH, TOEPP, TOEPHP)

!!! note
    カテゴリカル因子はデフォルトで `FullDummyCoding()` でコーディングされます。他のコントラストコーディングには `coding` を使用してください。


# 例

```julia
VarEffect(@covstr(1+factor|subject), CSH)

VarEffect(@covstr(1 + formulation|subject), CSH; coding = Dict(:formulation => StatsModels.DummyCoding()))
```
