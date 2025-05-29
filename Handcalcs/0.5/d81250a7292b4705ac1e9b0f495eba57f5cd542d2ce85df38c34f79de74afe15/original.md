```
@handcalc expression
```

Create `LaTeXString` representing `expression`. The expression being a vaiable followed by an equals sign and an algebraic equation. Any side effects of the expression, like assignments, are evaluated as well. The RHS can be formatted or otherwise transformed by supplying a function as kwarg `post`.

# Examples

```julia-repl
julia> a = 2
2
julia> b = 5
5
julia> @handcalc c = a + b
L"$c = a + b = 2 + 5 = 7$"

julia> c
7
```
