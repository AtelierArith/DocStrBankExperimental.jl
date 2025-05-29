```
int(x)
```

The positional integer of the `CategoricalString` or `CategoricalValue` `x`, in the ordering defined by the pool of `x`. The type of `int(x)` is the reference type of `x`.

Not to be confused with `x.ref`, which is unchanged by reordering of the pool of `x`, but has the same type.

```
int(X::CategoricalArray)
int(W::Array{<:CategoricalString})
int(W::Array{<:CategoricalValue})
```

Broadcasted versions of `int`.

```julia-repl
julia> v = categorical(["c", "b", "c", "a"])
4-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "c"
 "b"
 "c"
 "a"

julia> levels(v)
3-element Vector{String}:
 "a"
 "b"
 "c"

julia> int(v)
4-element Vector{UInt32}:
 0x00000003
 0x00000002
 0x00000003
 0x00000001
```

See also: [`decoder`](@ref).
