```
project(M::MultinomialSymmetric, p, Y)
```

Project `Y` onto the tangent space at `p` on the [`MultinomialSymmetric`](@ref) `M`, return the result in `X`.

The formula from [DouikHassibi:2019](@cite), Sec. VI reads

$$
    \operatorname{proj}_p(Y) = Y - (α\mathbf{1}_n^{\mathrm{T}} + \mathbf{1}_n α^{\mathrm{T}}) ⊙ p,
$$

where $⊙$ denotes the Hadamard or elementwise product and $\mathbb{1}_n$ is the vector of length $n$ containing ones. The two vector $α ∈ ℝ^{n×n}$ is given by solving

$$
    (I_n+p)α =  Y\mathbf{1},
$$

where $I_n$ is teh $n×n$ unit matrix and $\mathbf{1}_n$ is the vector of length $n$ containing ones.
