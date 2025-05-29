```
expr_map(f, c...; skip_nothing::Bool=false)
```

Similar to `Base.map`, but expects `f` to return an expression, and will concanate these expression as a `Expr(:block, ...)` expression.

Skip `nothing` if `skip_nothing` is `true`.

# Example

```jldoctest
julia> expr_map(1:10, 2:11) do i,j
           :(1 + $i + $j)
       end
quote
    1 + 1 + 2
    1 + 2 + 3
    1 + 3 + 4
    1 + 4 + 5
    1 + 5 + 6
    1 + 6 + 7
    1 + 7 + 8
    1 + 8 + 9
    1 + 9 + 10
    1 + 10 + 11
end
```
