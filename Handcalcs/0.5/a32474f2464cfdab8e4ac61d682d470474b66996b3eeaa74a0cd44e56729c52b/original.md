```
@handcalcs(expressions, kwargs)
```

Create `LaTeXString` representing `expressions`. The expressions representing a number of expressions. A single expression being a vaiable followed by an equals sign and an algebraic equation. Any side effects of the expression, like assignments, are evaluated as well.   The RHS can be formatted or otherwise transformed by supplying a function as kwarg `post`. Can also add comments to the end of equations. See example below.

## Kwargs

  * cols: sets the number of columns in the output
  * spa: sets the line spacing
  * len: can set to `:long` and it will split equation to multiple lines
  * color: change the color of the output (`:blue`, `:red`, etc)
  * h_env: choose between "aligned" (default), "align" and other LaTeX options
  * not_funcs: name the functions you do not want to "unroll"

# Examples

```julia-repl
julia> a = 2
2

julia> b = 5
5

julia> e = 7
7

julia> @handcalcs begin 
    c = a + b; "eq 1";
    d = a - c
    e
end
L"$\begin{aligned}
c &= a + b = 2 + 5 = 7\;\text{  }(\text{eq 1})
\\[10pt]
d &= a - c = 2 - 7 = -5
\\[10pt]
e &= 7
\end{aligned}$"

julia> c
7

julia> d
-5

```
