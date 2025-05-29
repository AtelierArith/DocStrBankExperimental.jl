```
 (graph,crefs)=graph_horner(a; input=:A, B=:B, C=:C, scaling=1.0)
```

Generates the graph for the polynomial using Horner's method. More precisely, it corresponds to the evaluation of the polynomial

```
p(s) = a[1] + a[2]*(αs) + ... + a[n-1]*(αs)^(n-2) + a[n]*(αs)^(n-1),
```

as the recursion

```
Cj=s*B{j+1}
Bj=a[j]*I+α*Cj,
```

where `α=scaling`.

The kwargs `B` and `C` specifies the base-names of these intermediate variables.
