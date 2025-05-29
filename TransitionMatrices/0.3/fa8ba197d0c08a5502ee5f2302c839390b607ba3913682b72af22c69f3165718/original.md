```
RandomOrientationTransitionMatrix(𝐓::AbstractTransitionMatrix{CT, N}) where {CT, N}
```

Calculate the random-orientation T-Matrix according to Eq. (5.96) in Mishchenko et al. (2002).

$$
\left\langle T_{m n m^{\prime} n^{\prime}}^{k l}(L)\right\rangle=\frac{\delta_{n n^{\prime}} \delta_{m m^{\prime}}}{2 n+1} \sum_{m_1=-n}^n T_{m_1 n m_1 n}^{k l}(P), \quad k, l=1,2
$$
