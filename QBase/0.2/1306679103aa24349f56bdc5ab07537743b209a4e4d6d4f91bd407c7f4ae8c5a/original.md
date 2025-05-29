```
bell_kets() :: Vector{Ket{Float64}}
```

The Bell basis kets for maximally entangled bipartite qubit systems. These kets are ordered as $\{|\Phi^+\rangle, |\Phi^-\rangle, |\Psi^+\rangle, |\Psi^-\rangle \}$, where

$$
\begin{matrix}
    |\Phi^+\rangle = \frac{1}{\sqrt{2}}(|00\rangle + |11\rangle), &
|\Phi^-\rangle = \frac{1}{\sqrt{2}}(|00\rangle - |11\rangle), \\
    |\Psi^+\rangle = \frac{1}{\sqrt{2}}(|01\rangle + |10\rangle), &
    |\Psi^-\rangle = \frac{1}{\sqrt{2}}(|01\rangle - |10\rangle). \\
\end{matrix}
$$
