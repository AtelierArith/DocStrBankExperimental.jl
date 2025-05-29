```
midrad(::Type{TN}, mid, rad) where TN<:ThickNumber
```

Construct a `TN` from its midpoint `mid` and radius `rad`.

# Interface requirements

If

```julia
x = midrad(TN, mid, rad)
```

succeeds without throwing an error and `rad >= 0`, then it is required that

```julia
typeof(x) <: TN
rad(x) >= rad && rad(x) ≈ rad
```

If `rad < 0`, then it is required that

```julia
typeof(x) <: TN
isempty(x)
```
