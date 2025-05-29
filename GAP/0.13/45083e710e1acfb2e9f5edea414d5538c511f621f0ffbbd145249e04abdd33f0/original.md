```
FFE
```

Wrap a pointer to a GAP FFE ("finite field element") immediate object. This type is defined in the JuliaInterface C code.

# Examples

```jldoctest
julia> x = GAP.Globals.Z(3)
GAP: Z(3)

julia> typeof(x)
FFE
```
