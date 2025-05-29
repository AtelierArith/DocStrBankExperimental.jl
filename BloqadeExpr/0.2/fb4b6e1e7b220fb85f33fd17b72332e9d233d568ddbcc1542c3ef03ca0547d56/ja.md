```
XPhase_1r{T} <: PrimitiveBlock{3}
```

XPhase演算子は3レベルのライデバーグシステムに対して|1⟩と|r⟩に作用します。

$$
e^{ϕ ⋅ i} |1⟩⟨r| + e^{-ϕ ⋅ i} |r⟩⟨1| = 
\begin{pmatrix}
0 & 0 & 0 \\
0 & 0 & e^{ϕ ⋅ im} \\
0 & e^{-ϕ ⋅ im} & 0
\end{pmatrix}
$$
