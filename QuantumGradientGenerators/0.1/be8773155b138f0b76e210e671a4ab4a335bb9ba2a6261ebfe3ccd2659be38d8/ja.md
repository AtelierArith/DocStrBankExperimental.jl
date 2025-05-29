動的勾配のための拡張状態ベクトル。

```julia
Ψ̃ = GradVector(Ψ, num_controls)
```

初期状態 `Ψ` と `num_controls` 制御フィールドに対して。

`GradVector` は概念的に直接和（ブロック）列ベクトル $Ψ̃ = (|Ψ̃₁⟩, |Ψ̃₂⟩, … |Ψ̃ₙ⟩, |Ψ⟩)^T$ に対応し、ここで $n$ は `num_controls` です。ドキュメントの [`GradGenerator`](@ref) にあるように、対応する $G̃$ があれば、

$$
G̃ Ψ̃ = \begin{pmatrix}
Ĥ |Ψ̃₁⟩ + Ĥ₁|Ψ⟩ \\
\vdots \\
Ĥ |Ψ̃ₙ⟩ + Ĥₙ|Ψ⟩ \\
Ĥ |Ψ⟩
\end{pmatrix}
$$

および

$$
e^{-i G̃ dt} \begin{pmatrix} 0 \\ \vdots \\ 0 \\ |Ψ⟩ \end{pmatrix}
= \begin{pmatrix}
\frac{∂}{∂ϵ₁} e^{-i Ĥ dt} |Ψ⟩ \\
\vdots \\
\frac{∂}{∂ϵₙ} e^{-i Ĥ dt} |Ψ⟩ \\
e^{-i Ĥ dt} |Ψ⟩
\end{pmatrix}.
$$

初期化時に、$|Ψ̃₁⟩…|Ψ̃ₙ⟩$ はゼロです。
