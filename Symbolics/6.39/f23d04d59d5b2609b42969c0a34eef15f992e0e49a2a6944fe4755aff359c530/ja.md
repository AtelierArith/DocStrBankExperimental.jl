```
series(cs, x, [x0=0,], ns=0:length(cs)-1)
```

`cs`の係数を持つ`x`の周りの`x0`での冪級数を、冪`ns`に対して返します。

```
series(y, x, [x0=0,] ns)
```

変数`y`から自動的に作成された係数を持つ`x`の周りの`x0`での冪級数を、冪`ns`に対して返します。

# 例

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
