Parse a wiring diagram from a Julia program.

For the most part, this is standard Julia code but a few liberties are taken with the syntax. Products are represented as tuples. So if `x` and `y` are variables of type $X$ and $Y$, then `(x,y)` has type $X ⊗ Y$. Also, both `()` and `nothing` are interpreted as the monoidal unit $I$.

Unlike standard Julia, the function call expressions `f(x,y)` and `f((x,y))` are equivalent. Consequently, given morphisms $f: W → X ⊗ Y$ and $g: X ⊗ Y → Z$, the code

```julia
x, y = f(w)
g(x,y)
```

is equivalent to `g(f(w))`. In standard Julia, at most one of these calls to `g` would be valid, unless `g` had multiple signatures.

The diagonals (copying and deleting) of a cartesian category are implicit in the Julia syntax: copying is variable reuse and deleting is variable non-use. For the codiagonals (merging and creating), a special syntax is provided, reinterpreting Julia's vector literals. The merging of `x1` and `x2` is represented by the vector `[x1,x2]` and creation by the empty vector `[]`. For example, `f([x1,x2])` translates to `compose(mmerge(X),f)`.

This macro is a wrapper around [`parse_wiring_diagram`](@ref).
