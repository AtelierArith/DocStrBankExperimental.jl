```
unit_group(K::PadicField; n_quo::Int = -1) -> FinGenAbGroup, Map
```

Returns a group $U$ and a map $f: U \to\K^*$. $U$ is an approximation to the unit group up to the precision of $K$. More precisely, if `K^* = \langle p\rangle  \times \mathbbb F_p^* \times 1+p\mathbbb Z_p` Then $U$ will be isomorphic to $\mathbbb Z \times \mathbbb Z/(p-1) \times \mathbbb Z/p^(k-1)$.

If `n_quo` is given and positive, then $\mathbbb F_p^*$ will be replaced by the quotient modulo `n_quo`-th powers. (To avoid the costly discrete logarithm in the finite field)
