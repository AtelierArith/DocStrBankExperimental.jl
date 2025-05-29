```
alg_equations(sys::AbstractSystem)
```

For a system, returns a vector of all its algebraic equations (i.e. that does not contain any differentials).

Example: ```julia using ModelingToolkit using ModelingToolkit: t*nounits as t, D*nounits as D @parameters p d @variables X(t) eq1 = D(X) ~ p - d*X eq2 = 0 ~ p - d*X @named osys = ODESystem([eq1, eq2], t)

alg_equations(osys) # returns `[0 ~ p - d*X(t)]`.
