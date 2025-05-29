```
Reality <: Enum{Int8}
```

Enum type with instances

```
REAL = 1
PSEUDOREAL = -1
COMPLEX = 0
```

The return value of [`reality(::AbstractIrrep)`](@ref) and [`calc_reality`](@ref) is an instance of `Reality`. The reality type of an irrep is relevant for constructing "physically real" irreps (co-reps) via [`realify`](@ref).
