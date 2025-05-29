```
EarthMoverDistance <: SignaturesDM
```

Earth Mover Distance discriminant measure for the Signatures energy map.

Equation: 

$E(P,Q) = \frac{\sum_{k=1}^{m+n+1} |\hat p_k - \hat q_k| (r_{k+1} - r_k)}{w_\Sigma}$

where 

  * $r_1, r_2, \ldots, r_{m+n}$ is the sorted list of $p_1, \ldots, p_m, q_1, \ldots, q_n$
  * $\hat p_k = \sum_{p_i \leq r_k} w_{p_i}$
  * $\hat q_k = \sum_{q_i \leq r_k} w_{q_i}$
