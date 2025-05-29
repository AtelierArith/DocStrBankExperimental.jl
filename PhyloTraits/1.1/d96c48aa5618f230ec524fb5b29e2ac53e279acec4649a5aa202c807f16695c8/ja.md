```
EqualRatesSubstitutionModel(numberStates, α, labels)
```

[`TraitSubstitutionModel`](@ref) は、任意の数の状態とすべての状態間の等しい置換率 α を持つ特性のためのモデルです。デフォルトのラベルは "1","2",...

# 例

```jldoctest
julia> m1 = EqualRatesSubstitutionModel(2, [1.0], ["low","high"])
Equal Rates Substitution Model with k=2,
all rates equal to α=1.0.
rate matrix Q:
             low    high
     low       *  1.0000
    high  1.0000       *
```
