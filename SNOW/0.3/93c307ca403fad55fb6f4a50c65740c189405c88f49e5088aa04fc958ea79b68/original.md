```
minimize(func!, x0, ng, lx=-Inf, ux=Inf, lg=-Inf, ug=0.0, options=Options())
```

solve the optimization problem

$\text{minimize} \quad    f(x) \\$ $\text{subject to} \quad  l_g \le g(x) \le u_g \\$ $\quad\quad\quad\quad   l_x \le x \le u_x$

`f = func!(g, x)`, unless user-supplied derivatives then: `f = func!(g, df, dg, x)`

equality constraint for the ith constraint: `lg[i] = ug[i]`
