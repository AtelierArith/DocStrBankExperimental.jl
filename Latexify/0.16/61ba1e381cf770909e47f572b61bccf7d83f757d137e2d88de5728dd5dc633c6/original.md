```
@latexrun expression
```

Latexify and evaluate `expression`. Useful for expressions with side effects, like assignments.

# Examples

```julia-repl
julia> @latexrun y = 3/2 + $(3/2)
L"$y = \frac{3}{2} + 1.5$"

julia> y
3.0
```

See also [`@latexify`](@ref), [`@latexdefine`](@ref).
