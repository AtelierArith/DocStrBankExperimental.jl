```
get_coherence(ψ::QuantumObject)
```

Get the coherence value $\alpha$ by measuring the expectation value of the destruction operator $\hat{a}$ on a state $\ket{\psi}$ or a density matrix $\hat{\rho}$.

It returns both $\alpha$ and the corresponding state with the coherence removed: $\ket{\delta_\alpha} = \exp ( \alpha^* \hat{a} - \alpha \hat{a}^\dagger ) \ket{\psi}$ for a pure state, and $\hat{\rho_\alpha} = \exp ( \alpha^* \hat{a} - \alpha \hat{a}^\dagger ) \hat{\rho} \exp ( -\bar{\alpha} \hat{a} + \alpha \hat{a}^\dagger )$ for a density matrix. These states correspond to the quantum fluctuations around the coherent state $\ket{\alpha}$ or $|\alpha\rangle\langle\alpha|$.
