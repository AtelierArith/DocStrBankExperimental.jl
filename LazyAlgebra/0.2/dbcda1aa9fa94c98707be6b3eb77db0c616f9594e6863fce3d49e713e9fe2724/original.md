```
Jacobian(A,x) -> obj
```

yields an object instance `obj` representing the Jacobian `∇(A,x)` of the non-linear mapping `A` for the variables `x`.

Directly calling this constructor is discouraged, call [`jacobian(A,x)`](@ref) or [`∇(A,x)`](@ref) instead and benefit from automatic simplification rules.
