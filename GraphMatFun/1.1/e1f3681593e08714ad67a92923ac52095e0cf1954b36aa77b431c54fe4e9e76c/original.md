```
 (graph,crefs)=graph_newton_schulz(
    k,
    T = ComplexF64;
    input = :A,
    Z = :Z,
    Q = :Q,
    V = :V,
)
```

Does `k` iterations of the Newton–Schulz iteration for approximating the inverse of a matrix A (name given by `input`), i.e., the recursion

```
V_k+1 = V_k*(2*I - A*V_k),
```

with `V_0=A`. The recursion is implemented using the graph operations

```
Z_i=A*V_i
Q_i=2*I-Z_i
V_{i+1}=V_i*Q_i,
```

and the kwargs `Z`, `Q`, and `V` determines the naming of the corresponding intermediate steps.

**References**

1. G. Schulz. "Iterative Berechnung der reziproken Matrix". Zeitschrift für Angewandte Mathematik und Mechanik, 13:57–59, 1933. DOI: [10.1002/zamm.19330130111](https://doi.org/10.1002/zamm.19330130111)
2. N. J. Higham. "Functions of Matrices". SIAM, Philadelphia, PA, 2008. DOI: [10.1137/1.9780898717778](https://doi.org/10.1137/1.9780898717778)
