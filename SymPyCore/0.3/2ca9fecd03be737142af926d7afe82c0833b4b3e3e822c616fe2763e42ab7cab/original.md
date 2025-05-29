```
solve
```

Use `solve` to solve algebraic equations.

# Extended help

Examples:

```jldoctest mathfuns
julia> using SymPyPythonCall


julia> @syms x y a b c d
(x, y, a, b, c, d)

julia> solve(x^2 + 2x + 1, x) # [-1]
1-element Vector{Sym{PythonCall.Py}}:
 -1

julia> solve(x^2 + 2a*x + a^2, x) # [-a]
1-element Vector{Sym{PythonCall.Py}}:
 -a

julia> u = solve([a*x + b*y-3, c*x + b*y - 1], [x,y]); show(u[x])
2/(a - c)
```

!!! note
    A very nice example using `solve` is a [blog](https://newptcai.github.io/euclidean-plane-geometry-with-julia.html) entry on [Napoleon's theorem](https://en.wikipedia.org/wiki/Napoleon%27s_theorem) by Xing Shi Cai.


!!! note "Systems"
    Use a tuple, not a vector, of equations when there is more than one.

