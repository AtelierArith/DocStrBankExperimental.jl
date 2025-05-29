```
XPhase_01{T} <: PrimitiveBlock{3}
```

XPhase演算子は3レベルのライデバーグシステムに対して|0⟩と|1⟩に作用します。

$$
e^{ϕ ⋅ i} |0⟩⟨1| + e^{-ϕ ⋅ i} |1⟩⟨0| = 
\begin{pmatrix}
0 & e^{ϕ ⋅ im} & 0 \\
e^{-ϕ ⋅ im} & 0 & 0 \\
0 & 0 & 0
\end{pmatrix}
$$
