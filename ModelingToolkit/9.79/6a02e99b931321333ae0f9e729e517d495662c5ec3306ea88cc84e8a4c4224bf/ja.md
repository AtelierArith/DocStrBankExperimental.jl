```
has_diff_eqs(sys::AbstractSystem)
```

システムに少なくとも1つの微分方程式（すなわち、微分項を含む方程式）が含まれている場合は `true` を返します。これはサブシステムを考慮せず、トップレベルのシステム内の方程式のみを考慮します。

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

has_diff_eqs(osys12) # returns `true`.
has_diff_eqs(osys21) # returns `false`.
```
