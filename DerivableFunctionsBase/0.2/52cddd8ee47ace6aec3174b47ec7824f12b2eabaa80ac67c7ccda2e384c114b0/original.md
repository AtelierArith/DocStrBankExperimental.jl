```
DerivableFunction(F::Function; ADmode::Union{Val,Symbol}=Val(:Symbolic))
DerivableFunction(F::Function, testinput::Union{Number,AbstractVector{<:Number}}; ADmode::Union{Val,Symbol}=Val(:Symbolic))
DerivableFunction(F::Function, dF::Function; ADmode::Union{Val,Symbol}=Val(:Symbolic))
DerivableFunction(F::Function, dF::Function, ddF::Function)
```

Stores derivatives of a given function (as well as input-output dimensions) for potentially faster computations when derivatives are known.
