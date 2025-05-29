```
alg_equations(sys::AbstractSystem)
```

システムに対して、そのすべての代数方程式のベクトルを返します（すなわち、微分を含まないもの）。

例: ```julia using ModelingToolkit using ModelingToolkit: t*nounits as t, D*nounits as D @parameters p d @variables X(t) eq1 = D(X) ~ p - d*X eq2 = 0 ~ p - d*X @named osys = ODESystem([eq1, eq2], t)

alg_equations(osys) # returns `[0 ~ p - d*X(t)]`. ```
