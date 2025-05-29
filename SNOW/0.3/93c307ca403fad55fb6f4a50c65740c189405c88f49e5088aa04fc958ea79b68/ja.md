```
最小化(func!, x0, ng, lx=-Inf, ux=Inf, lg=-Inf, ug=0.0, options=Options())
```

最適化問題を解く

$$
\text{最小化} \quad    f(x) \\
$$

$\text{制約条件} \quad  l_g \le g(x) \le u_g \\$ $\quad\quad\quad\quad   l_x \le x \le u_x$

`f = func!(g, x)`、ユーザーが供給した導関数がある場合は: `f = func!(g, df, dg, x)`

$$
i
$$

番目の制約の等式制約: `lg[i] = ug[i]`
