````
greensfunctions_col(j::Integer,σ::Array{ComplexF64,1},A)

Calculate the multiplication of the Green's function G and the vector b:
```math

[G(\sigma_k) b]_i = \left[ (\sigma_k I - A)^{-1} b \right]_{i},
```
with the use of the shifted conjugate gradient method
(See, Y. Nagai, Y. Shinohara, Y. Futamura, and T. Sakurai,[arXiv:1607.03992v2 or DOI:10.7566/JPSJ.86.014708]).
One can obtain ``[G(\sigma_k) b]_i`` with different frequencies ``\sigma_k``, simultaneously.

Inputs:

* `σ` :frequencies

* `A` :hermitian matrix. We can use Arrays,LinearMaps, SparseArrays

* `b` :input vector

* `eps` :residual (optional) Default:`1e-12`

* `maximumsteps` : maximum number of steps (optional) Default:`20000`

Output:
* `Gij[1:M,1:size(A)[1]]`: the matrix elements Green's functions of j-th col at M frequencies defined by ``\sigma_k``.
````
