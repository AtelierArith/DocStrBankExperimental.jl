```
XPhase_1r{T} <: PrimitiveBlock{3}
```

XPhase operator act on |1⟩ and |r⟩ for 3-level Rydberg system.

$$
e^{ϕ ⋅ i} |1⟩⟨r| + e^{-ϕ ⋅ i} |r⟩⟨1| = 
\begin{pmatrix}
0 & 0 & 0 \\
0 & 0 & e^{ϕ ⋅ im} \\
0 & e^{-ϕ ⋅ im} & 0
\end{pmatrix}
$$
