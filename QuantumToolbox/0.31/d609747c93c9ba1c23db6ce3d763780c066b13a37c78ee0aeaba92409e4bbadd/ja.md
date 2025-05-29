```
get_coherence(ψ::QuantumObject)
```

コヒーレンス値 $\alpha$ を、状態 $\ket{\psi}$ または密度行列 $\hat{\rho}$ に対する消失演算子 $\hat{a}$ の期待値を測定することで取得します。

これは、純粋状態に対しては $\ket{\delta_\alpha} = \exp ( \alpha^* \hat{a} - \alpha \hat{a}^\dagger ) \ket{\psi}$、密度行列に対しては $\hat{\rho_\alpha} = \exp ( \alpha^* \hat{a} - \alpha \hat{a}^\dagger ) \hat{\rho} \exp ( -\bar{\alpha} \hat{a} + \alpha \hat{a}^\dagger )$ の両方の $\alpha$ と、コヒーレンスが除去された対応する状態を返します。これらの状態は、コヒーレント状態 $\ket{\alpha}$ または $|\alpha\rangle\langle\alpha|$ の周りの量子ゆらぎに対応します。
