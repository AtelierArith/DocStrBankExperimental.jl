```
TensorMap(data::AbstractArray, codomain::ProductSpace{S,N₁}, domain::ProductSpace{S,N₂};
                tol=sqrt(eps(real(float(eltype(data)))))) where {S<:ElementarySpace,N₁,N₂}
TensorMap(data, codomain ← domain; tol=sqrt(eps(real(float(eltype(data))))))
TensorMap(data, domain → codomain; tol=sqrt(eps(real(float(eltype(data))))))
```

Construct a `TensorMap` from a plain multidimensional array.

## Arguments

  * `data::DenseArray`: tensor data as a plain array.
  * `codomain::ProductSpace{S,N₁}`: the codomain as a `ProductSpace` of `N₁` spaces of type `S<:ElementarySpace`.
  * `domain::ProductSpace{S,N₂}`: the domain as a `ProductSpace` of `N₂` spaces of type `S<:ElementarySpace`.
  * `tol=sqrt(eps(real(float(eltype(data)))))::Float64`:

Here, `data` can be specified in three ways:

1. `data` can be a `DenseVector` of length `dim(codomain ← domain)`; in that case it represents the actual independent entries of the tensor map. An instance will be created that directly references `data`.
2. `data` can be an `AbstractMatrix` of size `(dim(codomain), dim(domain))`
3. `data` can be an `AbstractArray` of rank `N₁ + N₂` with a size matching that of the domain and codomain spaces, i.e. `size(data) == (dims(codomain)..., dims(domain)...)`

In case 2 and 3, the `TensorMap` constructor will reconstruct the tensor data such that the resulting tensor `t` satisfies `data == convert(Array, t)`, up to an error specified by `tol`. For the case where `sectortype(S) == Trivial` and `data isa DenseArray`, the `data` array is simply reshaped into a vector and used as in case 1 so that the memory will still be shared. In other cases, new memory will be allocated.

Note that in the case of `N₁ + N₂ = 1`, case 3 also amounts to `data` being a vector, whereas when `N₁ + N₂ == 2`, case 2 and case 3 both require `data` to be a matrix. Such ambiguous cases are resolved by checking the size of `data` in an attempt to support all possible cases.

!!! note
    This constructor for case 2 and 3 only works for `sectortype` values for which conversion to a plain array is possible, and only in the case where the `data` actually respects the specified symmetry structure, up to a tolerance `tol`.

