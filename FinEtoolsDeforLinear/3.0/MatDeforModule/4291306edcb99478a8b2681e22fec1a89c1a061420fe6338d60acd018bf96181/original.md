```
tens4dot2!(R::Array{T, 2}, F::Array{T, 4}, S::Array{T, 2}) where {T}
```

Compute the double contraction of a 4th-order and a 2nd-order tensors.

!!! note



The double contraction  of two second-order sensors is defined as  `A:B = tr(A'*B) = A_ij B_ij`

The resulting second-order tensor is first zeroed out, and then the result is accumulated.
