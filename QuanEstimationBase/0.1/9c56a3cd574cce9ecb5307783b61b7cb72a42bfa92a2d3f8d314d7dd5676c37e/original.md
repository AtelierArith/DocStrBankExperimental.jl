```
CFIM_obj(;M=nothing, W=nothing, eps=GLOBAL_EPS)
```

Choose CFI [$\mathrm{Tr}(WI^{-1})$] as the objective function with $W$ the weight matrix and $I$ the CFIM.

  * `M`: A set of positive operator-valued measure (POVM). The default measurement is a set of rank-one symmetric informationally complete POVM (SIC-POVM).
  * `W`: Weight matrix.
  * `eps`: Machine epsilon.
