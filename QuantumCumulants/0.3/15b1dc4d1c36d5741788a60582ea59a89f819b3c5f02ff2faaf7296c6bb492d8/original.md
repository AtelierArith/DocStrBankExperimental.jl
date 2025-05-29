```
IndexedVariable <: CNumber
IndexedVariable(name::Symbol,ind::Index)
IndexedVariable(name::Symbol,ind1::Index,ind2:Index)
```

A indexed symbolic variable. The variable can (once equations are calculated) be easily exchanged for numerical values. Calling a IndexedVariable using two different [`Index`](@ref) objects one can create [`DoubleIndexedVariable`](@ref) objects. See also: [`value_map`](@ref)
