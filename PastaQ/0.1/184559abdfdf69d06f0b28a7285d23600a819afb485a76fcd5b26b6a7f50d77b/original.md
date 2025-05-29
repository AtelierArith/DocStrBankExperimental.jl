```
fidelity(A::MPO, B::MPO; process::Bool = false, cutoff::Float64 = 1e-15)
```

Fidelity $F$ between two MPOs $A$ and $B$. Implements the following:

1. If $A$ and $B$ are density operators, $F$ is the full quantum state fidelity

$$
F(\rho,\sigma) = \Big(\text{Tr}\sqrt{\sqrt{\rho}\sigma\sqrt{\rho}}\Big)^2.
$$

Note: this scales exponentially with the number $n$ of qubits, as it involves a full diagonalization.

2. If $A$ and $B$ are unitary operators (i.e. rank-1 channels) and `process = true`,

$F$ is the process fidelity

$$
F = 2^{-2n} \text{Tr}(A^\dagger B) = 2^{-2n} |\langle\Phi_A|\Phi_B\rangle|^2,
$$

where $|\Phi_j\rangle = |j\rangle\rangle$ is the MPS corresponding to the vectorization of the unitary operator.

3. If $A$ is a Choi matrix and `B` is a unitary operator (or viceversa), return the process fidelity

$$
F = 2^{-2n} \text{Tr}(A |\Phi_B\rangle\langle\Phi_B|) = \langle\Phi_B|A|\Phi_B\rangle.
$$

4. If $A$ and $B$ are both Choi matrices, return the full process fidelity

$$
F(A,B) = 2^{-2n}\Big(\text{Tr}\sqrt{\sqrt{A}B\sqrt{A}}\Big)^2.
$$

which, as above, scale exponentially with $n$.
