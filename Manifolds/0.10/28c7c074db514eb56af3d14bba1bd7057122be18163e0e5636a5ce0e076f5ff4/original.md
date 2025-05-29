```
exp(M::Stiefel, p, X)
```

Compute the exponential map on the [`Stiefel`](@ref)`{n,k,𝔽}`() manifold `M` emanating from `p` in tangent direction `X`.

$$
\exp_p X = \begin{pmatrix}
   p\\X
 \end{pmatrix}
 \operatorname{Exp}
 \left(
 \begin{pmatrix} p^{\mathrm{H}}X & - X^{\mathrm{H}}X\\
 I_n & p^{\mathrm{H}}X\end{pmatrix}
 \right)
\begin{pmatrix}  \exp( -p^{\mathrm{H}}X) \\ 0_n\end{pmatrix},
$$

where $\operatorname{Exp}$ denotes matrix exponential, $⋅^{\mathrm{H}}$ denotes the complex conjugate transpose or Hermitian, and $I_k$ and $0_k$ are the identity matrix and the zero matrix of dimension $k×k$, respectively.
