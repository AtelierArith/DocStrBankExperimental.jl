```
sic_qubit_kets() :: Vector{Ket{Complex{Float64}}}
```

対称情報完全（SIC）キュービットの四重項。このキュービットのセットは、ブロッホ球に内接する四面体の頂点に対応します。

$$
\begin{matrix}
    |\psi_1\rangle = |0\rangle, & \quad |\psi_2\rangle = \frac{1}{\sqrt{3}}|0\rangle + \sqrt{\frac{2}{3}}|1\rangle, \\
    |\psi_3\rangle = \frac{1}{\sqrt{3}}|0\rangle + \sqrt{\frac{2}{3}} e^{i 2\pi/3}|1\rangle, & \quad |\psi_4\rangle = \frac{1}{\sqrt{3}}|0\rangle + \sqrt{\frac{2}{3}} e^{i 4\pi/3}|1\rangle
\end{matrix}
$$
