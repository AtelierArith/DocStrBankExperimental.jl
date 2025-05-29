```
project(M::MultinomialDoubleStochastic, p, Y)
```

Project `Y` onto the tangent space at `p` on the [`MultinomialDoubleStochastic`](@ref) `M`, return the result in `X`. The formula reads

$$
    \operatorname{proj}_p(Y) = Y - (α\mathbf{1}_n^{\mathrm{T}} + \mathbf{1}_nβ^{\mathrm{T}}) ⊙ p,
$$

where $⊙$ denotes the Hadamard or elementwise product and $\mathbb{1}_n$ is the vector of length $n$ containing ones. The two vectors $α,β ∈ ℝ^{n×n}$ are computed as a solution (typically using the left pseudo inverse) of

$$
    \begin{pmatrix} I_n & p\\p^{\mathrm{T}} & I_n \end{pmatrix}
    \begin{pmatrix} α\\ β\end{pmatrix}
    =
    \begin{pmatrix} Y\mathbf{1}\\Y^{\mathrm{T}}\mathbf{1}\end{pmatrix},
$$

where $I_n$ is the $n×n$ unit matrix and $\mathbf{1}_n$ is the vector of length $n$ containing ones.
