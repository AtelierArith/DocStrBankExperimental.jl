```
has_alg_eqs(sys::AbstractSystem)
```

システムに対して、*トップレベルシステム*に少なくとも1つの代数方程式（すなわち、微分を含まない方程式）が含まれている場合はtrueを返します。

例：

```julia
using ModelingToolkit
using ModelingToolkit: t_nounits as t, D_nounits as D
@parameters p d
@variables X(t)
eq1 = D(X) ~ p - d*X
eq2 = 0 ~ p - d*X
@named osys1 = ODESystem([eq1], t)
@named osys2 = ODESystem([eq2], t)
osys12 = compose(osys1, [osys2])
osys21 = compose(osys2, [osys1])

has_alg_eqs(osys12) # returns `false`.
has_alg_eqs(osys21) # returns `true`.
```
