```
rotate(𝐓::AbstractTransitionMatrix{CT, N}, rot::Rotation{3})
```

Rotate the given T-Matrix `𝐓` by the Euler angle `rot` and generate a new T-Matrix.

For a general T-Matrix, Eq. (5.29) in Mishchenko et al. (2002) is used as a fallback. A `TransitionMatrix` will be returned, which is the most general yet concrete type.

$$
T_{m n m^{\prime} n^{\prime}}^{p p′}(L ; \alpha, \beta, \gamma)=\sum_{m_1=-n}^n \sum_{m_2=-n^{\prime}}^{n^{\prime}} D_{m m_1}^n(\alpha, \beta, \gamma) T_{m_1 n m_2 n^{\prime}}^{p p′}(P) D_{m_2 m^{\prime}}^{n^{\prime}}(-\gamma,-\beta,-\alpha)\quad p,p′=1,2
$$
