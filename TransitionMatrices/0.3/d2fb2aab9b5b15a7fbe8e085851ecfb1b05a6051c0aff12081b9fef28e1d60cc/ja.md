```
rotate(𝐓::AbstractTransitionMatrix{CT, N}, rot::Rotation{3})
```

与えられた T-Matrix `𝐓` をオイラー角 `rot` で回転させ、新しい T-Matrix を生成します。

一般的な T-Matrix に対しては、Mishchenko et al. (2002) の式 (5.29) がフォールバックとして使用されます。最も一般的でありながら具体的な型である `TransitionMatrix` が返されます。

$$
T_{m n m^{\prime} n^{\prime}}^{p p′}(L ; \alpha, \beta, \gamma)=\sum_{m_1=-n}^n \sum_{m_2=-n^{\prime}}^{n^{\prime}} D_{m m_1}^n(\alpha, \beta, \gamma) T_{m_1 n m_2 n^{\prime}}^{p p′}(P) D_{m_2 m^{\prime}}^{n^{\prime}}(-\gamma,-\beta,-\alpha)\quad p,p′=1,2
$$
