```
has_alg_equations(sys::AbstractSystem)
```

システムに対して、少なくとも1つの代数方程式（すなわち、微分を含まないもの）が含まれている場合はtrueを返します。

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

has_alg_equations(osys1) # returns `false`.
has_alg_equations(osys2) # returns `true`.
```
