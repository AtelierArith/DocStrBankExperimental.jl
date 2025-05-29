```
 (graph,crefs)=graph_horner_degopt(a; scaling=1.0, input=:A)
```

Generates a polynomial using Horner's evaluation scheme. The polynomial

```
 p(s) = a[1] + a[2]*(αs) + ... + a[n-1]*(αs)^(n-2) + a[n]*(αs)^(n-1),
```

is evaluated as

```
 p(s) = a[1] + (αs)*(a[2] + (αs)*(... + (αs)*(a[n-1] + a[n]*(αs))...)),
```

where α=`scaling`. However, the function uses a call to [`graph_degopt`](@ref), resulting in more degrees of freedom in `crefs`. See also [`graph_horner`](@ref).
