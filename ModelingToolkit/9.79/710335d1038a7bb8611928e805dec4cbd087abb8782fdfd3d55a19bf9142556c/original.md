```
diff_equations(sys::AbstractSystem)
```

For a system, returns a vector of all its differential equations (i.e. that does contain a differential).

Example: ```julia using ModelingToolkit using ModelingToolkit: t*nounits as t, D*nounits as D @parameters p d @variables X(t) eq1 = D(X) ~ p - d*X eq2 = 0 ~ p - d*X @named osys = ODESystem([eq1, eq2], t)

diff_equations(osys) # returns `[Differential(t)(X(t)) ~ p - d*X(t)]`.
