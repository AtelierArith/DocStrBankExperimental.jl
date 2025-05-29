```
solveset
```

Like `solve` but returns a set object. Finite sets are returned as `Set` objects in `Julia`. Infinite sets must be queried.

# Example

```
julia> @syms x
(x,)

julia> u = solveset(sin(x) ~ 1//2, x)
⎧        5⋅π │      ⎫   ⎧        π │      ⎫
⎨2⋅n⋅π + ───  │ n ∊ ℤ⎬ ∪ ⎨2⋅n⋅π + ─ │ n ∊ ℤ⎬
⎩         6  │      ⎭   ⎩        6 │      ⎭

julia> intersect(u, sympy.Interval(0, 2PI))
Set{Sym} with 2 elements:
  pi/6
  5*pi/6
```

[SymPy documentation](https://docs.sympy.org/latest/search.html?q=solveset&check_keywords=yes&area=default)
