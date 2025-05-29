```
bpa(X...)
```

Create a normalized basic probability assignment (BPA) structure from pairs of mass assignments `X`.

# Examples

```juliadoctest
julia> A = bpa(Set("a") => 0.1, Set("b") => 0.2)
Dict{Set{Char}, Float64} with 3 entries:
    Set(['a'])      => 0.1
    Set(['b'])      => 0.2
    Set(['a', 'b']) => 0.7
```

See also: [`BPA`](@ref).
