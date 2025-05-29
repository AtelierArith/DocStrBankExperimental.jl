```
DoubleIndexedVariable <: CNumber
DoubleIndexedVariable(name::Symbol,ind1::Index,ind2::Index;identical::Bool)
```

A double-indexed symbolic variable. The variable can (once equations are calculated) be easily exchanged for numerical values. See also: [`value_map`](@ref)

# Fields:

  * name: A Symbol, defining the name of the variable
  * ind1: The first Index of the variable
  * ind2: The second Index of the variable
  * identical: A Bool, defining if the variable can have non-zero main-diagonal terms, e.g: Γᵢᵢ ≠ 0 would be specified with true.
