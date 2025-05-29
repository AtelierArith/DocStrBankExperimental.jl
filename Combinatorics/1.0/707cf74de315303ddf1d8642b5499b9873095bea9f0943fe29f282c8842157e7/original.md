```
prevprod(a::Vector{Int}, x)
```

Previous integer not greater than `x` that can be written as $\prod k_i^{p_i}$ for integers $p_1$, $p_2$, etc.

For integers $i_1$, $i_2$, $i_3$, this is equivalent to finding the largest $x$ such that

$i_1^{n_1} i_2^{n_2} i_3^{n_3} \leq x$

for integers $n_1$, $n_2$, $n_3$.
