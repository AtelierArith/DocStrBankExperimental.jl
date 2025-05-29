```
solveset
```

`solve`と似ていますが、セットオブジェクトを返します。有限セットは`Julia`の`Set`オブジェクトとして返されます。無限セットはクエリする必要があります。

# 例

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
