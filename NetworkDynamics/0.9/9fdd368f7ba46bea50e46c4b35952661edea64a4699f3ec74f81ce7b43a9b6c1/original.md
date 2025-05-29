```
SymbolicView{N,VT} <: AbstractVetor{VT}
```

Is a (smallish) fixed size vector type with named dimensions. Its main purpose is to allow named acces to variables in [`ComponentCondition`](@ref) and [`ComponentAffect`](@ref) functions.

I.e. when the `ComponentAffect` declared `sym=[:x, :y]`, you can acces `u[:x]` and `u[:y]` inside the condition function.
