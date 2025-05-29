```
 (graph,crefs)=graph_ps(a; input=:A,
                      B_base=:B, C_base=:C, P_base=:P)
```

Generates the graph for the Paterson–Stockmeyer procedure with monomial basis coefficieents. More precisely, it corresponds to evaluation of the polynomial

```
p(s) = a[1] + a[2]*s + ... + a[n]*s^(n-1).
```

The code follows the description in the second of the papers referenced below.

**References**

1. M. Paterson and L. Stockmeyer. "On the number of nonscalar multiplications necessary to evaluate polynomials". SIAM Journal on Scientific Computing, 2(1):60-66, 1973. DOI: [10.1137/0202007](https://doi.org/10.1137/0202007)
2. M. Fasi. "Optimality of the Paterson–Stockmeyer method for evaluating matrix polynomials and rational matrix functions". Linear Algebra and its Applications, 574, 2019. DOI: [10.1016/j.laa.2019.04.001](https://doi.org/10.1016/j.laa.2019.04.001)
