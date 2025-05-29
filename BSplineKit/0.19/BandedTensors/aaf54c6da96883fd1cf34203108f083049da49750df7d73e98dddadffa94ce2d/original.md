```
BandedTensor3D{T,b}
```

Three-dimensional banded tensor with element type `T`.

# Extended help

## Band structure

The band structure is assumed to be symmetric, and is defined in terms of the band width $b$. For a cubic banded tensor of dimensions $N × N × N$, the element $A_{ijk}$ may be non-zero only if $|i - j| ≤ b$, $|i - k| ≤ b$ and $|j - k| ≤ b$.

## Storage

The data is stored as a `Vector` of small matrices, each with size $r × r$, where $r = 2b + 1$ is the total number of bands. Each submatrix holds the non-zero values of a slice of the form `A[:, :, k]`.

For $b = 2$, one of these matrices looks like the following, where dots indicate out-of-bands values (equal to zero):

```
| x  x  x  ⋅  ⋅ |
| x  x  x  x  ⋅ |
| x  x  x  x  x |
| ⋅  x  x  x  x |
| ⋅  ⋅  x  x  x |
```

These submatrices are stored as static matrices (`SMatrix`).

## Setting elements

To define the elements of the tensor, each slice `A[:, :, k]` must be set at once. For instance:

```julia
A = BandedTensor3D(undef, 20, Val(2))  # tensor of size 20×20×20 and band width b = 2
for k in axes(A, 3)
    A[:, :, k] = rand(5, 5)
end
```

See [`setindex!`](@ref) for more details.

## Non-cubic tensors

A slight departure from cubic tensors is currently supported, with dimensions of the form $N × N × M$. Moreover, bands may be shifted along the third dimension by an offset $δ$. In this case, the bands are given by $|i - j| ≤ b$, $|i - (k + δ)| ≤ b$ and $|j - (k + δ)| ≤ b$.

---

```
BandedTensor3D{T}(undef, (Ni, Nj, Nk), Val(b); [bandshift = (0, 0, 0)])
BandedTensor3D{T}(undef, N, Val(b); ...)
```

Construct 3D banded tensor with band widths `b`.

Right now, the first two dimension sizes `Ni` and `Nj` of the tensor must be equal. In the second variant, the tensor dimensions are `N × N × N`.

The tensor is constructed uninitialised. Each submatrix `A[:, :, k]` of size `(2b + 1, 2b + 1)`, for `k ∈ 1:Nk`, should be initialised as in the following example:

```
A[:, :, k] = rand(2b + 1, 2b + 1)
```

The optional `bandshift` argument should be a tuple of the form `(δi, δj, δk)` describing a band shift. Right now, band shifts are limited to `δi = δj = 0`, so this argument should actually look like `(0, 0, δk)`.
