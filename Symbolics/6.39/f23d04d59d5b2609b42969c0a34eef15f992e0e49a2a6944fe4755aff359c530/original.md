```
series(cs, x, [x0=0,], ns=0:length(cs)-1)
```

Return the power series in `x` around `x0` to the powers `ns` with coefficients `cs`.

```
series(y, x, [x0=0,] ns)
```

Return the power series in `x` around `x0` to the powers `ns` with coefficients automatically created from the variable `y`.

# Examples

```jldoctest
julia> @variables x y[0:3] z
3-element Vector{Any}:
 x
  y[0:3]
 z

julia> series(y, x, 2)
y[0] + (-2 + x)*y[1] + ((-2 + x)^2)*y[2] + ((-2 + x)^3)*y[3]

julia> series(z, x, 2, 0:3)
z[0] + (-2 + x)*z[1] + ((-2 + x)^2)*z[2] + ((-2 + x)^3)*z[3]
```
