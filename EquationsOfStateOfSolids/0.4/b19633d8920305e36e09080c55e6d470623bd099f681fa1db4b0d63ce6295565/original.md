```
orderof(x::FiniteStrainParameters)
```

Return the order of a `FiniteStrainParameters`.

# Examples

```jldoctest
julia> orderof(BirchMurnaghan(40, 0.5, 4, 0)) == 3
true
```
