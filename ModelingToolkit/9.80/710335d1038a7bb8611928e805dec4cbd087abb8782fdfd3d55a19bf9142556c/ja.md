```
diff_equations(sys::AbstractSystem)
```

システムに対して、その微分方程式のベクトルを返します（すなわち、微分を含むもの）。

例: ```julia using ModelingToolkit using ModelingToolkit: t*nounits as t, D*nounits as D @parameters p d @variables X(t) eq1 = D(X) ~ p - d*X eq2 = 0 ~ p - d*X @named osys = ODESystem([eq1, eq2], t)

diff_equations(osys) # returns `[Differential(t)(X(t)) ~ p - d*X(t)]`. ```
