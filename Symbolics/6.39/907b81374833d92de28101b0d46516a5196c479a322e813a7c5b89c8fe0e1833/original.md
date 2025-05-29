```
tosymbol(x::Union{Num,Symbolic}; states=nothing, escape=true) -> Symbol
```

Convert `x` to a symbol. `states` are the states of a system, and `escape` means if the target has escapes like `val"y(t)"`. If `escape` is false, then it will only output `y` instead of `y(t)`.

# Examples

```jldoctest
julia> @variables t z(t)
2-element Vector{Num}:
    t
 z(t)

julia> Symbolics.tosymbol(z)
Symbol("z(t)")

julia> Symbolics.tosymbol(z; escape=false)
:z
```
