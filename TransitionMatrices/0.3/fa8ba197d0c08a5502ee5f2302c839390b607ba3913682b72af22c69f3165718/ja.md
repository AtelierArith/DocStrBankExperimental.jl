```
RandomOrientationTransitionMatrix(𝐓::AbstractTransitionMatrix{CT, N}) where {CT, N}
```

Mishchenko et al. (2002) の式 (5.96) に従って、ランダムオリエンテーション T-行列を計算します。

$$
\left\langle T_{m n m^{\prime} n^{\prime}}^{k l}(L)\right\rangle=\frac{\delta_{n n^{\prime}} \delta_{m m^{\prime}}}{2 n+1} \sum_{m_1=-n}^n T_{m_1 n m_1 n}^{k l}(P), \quad k, l=1,2
$$
