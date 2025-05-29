```
rewrite_generator(expr::Expr, inner::Function)
```

Rewrites the generator statements `expr` and returns a properly nested for loop with nested filters as specified.

# Examples

```jldoctest
julia> using MutableArithmetics

julia> MutableArithmetics.rewrite_generator(:(i for i in 1:2 if isodd(i)), i -> :($i + 1))
:(for $(Expr(:escape, :(i = 1:2)))
      if $(Expr(:escape, :(isodd(i))))
          i + 1
      end
  end)
```
