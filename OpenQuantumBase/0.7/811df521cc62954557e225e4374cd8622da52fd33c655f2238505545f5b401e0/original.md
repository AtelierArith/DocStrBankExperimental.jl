```julia
haar_unitary(dim)

```

Generate a Haar random unitary matrix of dimension `(dim, dim)` using the QR decomposition method.

# Arguments

  * `dim::Int`: the dimension of the matrix.

# Returns

  * A Haar random unitary matrix of size `(dim, dim)`.

# Details

A Haar random unitary matrix is a matrix whose entries are complex numbers of modulus 1, chosen randomly with respect to the Haar measure on the unitary group U(dim). This implementation uses the QR decomposition method, where a complex Gaussian matrix of size `(dim, dim)` is generated, and then it is QR decomposed into the product of an orthogonal matrix and an upper triangular matrix with positive diagonal entries. The diagonal entries are then normalized by their absolute values to obtain the unitary matrix.

# Examples

```julia
julia> haar_unitary(3)
3×3 Matrix{ComplexF64}:
  0.407398+0.544041im   0.799456-0.213793im  -0.439273+0.396871im
 -0.690274-0.288499im   0.347444+0.446328im   0.426262+0.505472im
  0.437266-0.497024im  -0.067918-0.582238im   0.695026+0.186022im
```
