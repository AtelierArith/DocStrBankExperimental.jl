```
EqualRatesSubstitutionModel(numberStates, α, labels)
```

[`TraitSubstitutionModel`](@ref) for traits with any number of states and equal substitution rates α between all states. Default labels are "1","2",...

# example

```jldoctest
julia> m1 = EqualRatesSubstitutionModel(2, [1.0], ["low","high"])
Equal Rates Substitution Model with k=2,
all rates equal to α=1.0.
rate matrix Q:
             low    high
     low       *  1.0000
    high  1.0000       *
```
