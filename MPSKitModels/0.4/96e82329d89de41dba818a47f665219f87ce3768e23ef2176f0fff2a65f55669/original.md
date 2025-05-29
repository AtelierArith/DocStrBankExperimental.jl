```
classical_ising([elt::Type{<:Number}=ComplexF64], [symmetry::Type{<:Sector}=Trivial];
                beta=log(1+sqrt(2))/2)
```

MPO for the partition function of the two-dimensional classical Ising model, defined as

$$
\mathcal{Z}(\beta) = \sum_{\{s\}} \exp(-\beta H(s)) \text{ with } H(s) = -\sum_{\langle i, j \rangle} s_i s_j

$$

where each classical spin can take the values $s = \pm 1$.
