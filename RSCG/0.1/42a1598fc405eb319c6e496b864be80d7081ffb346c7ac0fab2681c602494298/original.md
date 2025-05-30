```
greensfunctions(vec_left::Array{<:Integer,1},j::Integer,σ::Array{ComplexF64,1},A)
```

Calculate the matrix element of the Green's function:

$$
G_{ij}(\sigma_k) = \left[ (\sigma_k I - A)^{-1} \right]_{ij},
$$

with the use of the reduced-shifted conjugate gradient method (See, Y. Nagai, Y. Shinohara, Y. Futamura, and T. Sakurai,[arXiv:1607.03992v2 or DOI:10.7566/JPSJ.86.014708]). One can obtain $G_{ij}(\sigma_k)$ with different frequencies $\sigma_k$, simultaneously.

Inputs:

  * `vec_left` :i indices of the Green's function
  * `j` :index of the Green's function
  * `σ` :frequencies
  * `A` :hermitian matrix. We can use Arrays,LinearMaps, SparseArrays
  * `eps` :residual (optional) Default:`1e-12`
  * `maximumsteps` : maximum number of steps (optional) Default:`20000`

Output:

  * `Gij[1:M,1:length(vec_left)]`: the matrix element Green's functions at M frequencies defined by $\sigma_k$.
