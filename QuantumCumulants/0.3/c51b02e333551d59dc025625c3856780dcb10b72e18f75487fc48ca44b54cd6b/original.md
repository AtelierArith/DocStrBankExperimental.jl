```
split_sums(term::SymbolicUtils.Symbolic,amount::Union{<:SymbolicUtils.Sym,<:Int64})
split_sums(me::MeanfieldEquations,amount)
```

Function, that splits sums inside a given term. The sums are split into a number of equal sums, specified in the `amount` argument, where in only one of the sums the dependencies for the indices (non equal indices) is considered.

# Arguments

*`me::MeanfieldEquations`: A [`MeanfieldEquations`](@ref) entity, which shall be evaluated, can also be any symbolic expression. *`amount::Union{<:SymbolicUtils.Sym,<:Int64}`: A Number or Symbolic determining, in how many terms a sum is split
