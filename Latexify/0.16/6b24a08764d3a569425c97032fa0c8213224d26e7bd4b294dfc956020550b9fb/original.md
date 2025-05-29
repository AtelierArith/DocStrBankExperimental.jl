```
@latexdefine expression
```

Latexify `expression`, followed by an equals sign and the return value of its evaluation. Any side effects of the expression, like assignments, are evaluated as well. The RHS can be formatted or otherwise transformed by supplying a function as kwarg `post`.

# Examples

```julia-repl
julia> @latexdefine y = 3/2 + $(3/2) env=:equation
L"\begin{equation}
y = \frac{3}{2} + 1.5 = 3.0
\end{equation}
"

julia> y
3.0

julia> @latexdefine y=π post=round
L"$x = \pi = 3.0$"
```

See also [`@latexify`](@ref), [`@latexrun`](@ref).
