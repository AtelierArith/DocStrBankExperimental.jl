```
bell_kets() :: Vector{Ket{Float64}}
```

最大エンタングルされた二項量子ビットシステムのためのベル基底ケット。これらのケットは $\{|\Phi^+\rangle, |\Phi^-\rangle, |\Psi^+\rangle, |\Psi^-\rangle \}$ の順に並べられています。ここで、

$$
\begin{matrix}
    |\Phi^+\rangle = \frac{1}{\sqrt{2}}(|00\rangle + |11\rangle), &
|\Phi^-\rangle = \frac{1}{\sqrt{2}}(|00\rangle - |11\rangle), \\
    |\Psi^+\rangle = \frac{1}{\sqrt{2}}(|01\rangle + |10\rangle), &
    |\Psi^-\rangle = \frac{1}{\sqrt{2}}(|01\rangle - |10\rangle). \\
\end{matrix}
$$
