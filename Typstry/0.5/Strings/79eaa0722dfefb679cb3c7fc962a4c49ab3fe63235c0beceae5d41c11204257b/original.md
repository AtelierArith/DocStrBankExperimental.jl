```
show_typst(x)
```

Print to `stdout` in Typst format with the default and custom [`context`](@ref)s.

# Examples

```jldoctest
julia> show_typst(1 // 2)
$1 / 2$

julia> show_typst(1:4)
$vec(
  1, 2, 3, 4
)$
```
