```
@handfunc expression
```

Create `LaTeXString` representing `expressions`. These expressions represent a number of expressions that exist within the function that was called. A single expression being a variable followed by an equals sign and the function being called. The expression is evaluated as well (not the expressions within the function). The RHS can be formatted or otherwise transformed by supplying a function as kwarg `post`.

# Examples

```julia-repl
julia> @handfunc Iy = calc_Ix(5, 15)
L"$\begin{aligned}
Ix &= \frac{b \cdot h^{3}}{12} = \frac{5 \cdot 15^{3}}{12} = 1406.25
\end{aligned}$"

julia> Iy
1406.25

```

Note how Iy is evaluated but Ix is not.
