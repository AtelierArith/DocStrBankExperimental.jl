```
@latexify expression
```

Create `LaTeXString` representing `expression`. Variables and expressions can be interpolated with `$`. Keyword arguments can be supplied to `latexify` by appending to the argument.

# Examples

```julia-repl
julia> @latexify x^2 + 3/2
L"$x^{2} + \frac{3}{2}$"

julia> @latexify x^2 + $(3/2)
L"$x^{2} + 1.5$"

julia> @latexify x^2 + 3/2 env=:raw
L"x^{2} + \frac{3}{2}"
```

See also [`latexify`](@ref), [`@latexrun`](@ref), [`@latexdefine`](@ref).
