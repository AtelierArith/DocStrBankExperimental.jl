```
tsvd(t::AbstractTensorMap, (leftind, rightind)::Index2Tuple;
    trunc::TruncationScheme = notrunc(), p::Real = 2, alg::Union{SVD, SDD} = SDD())
    -> U, S, V, ϵ
```

Compute the (possibly truncated) singular value decomposition such that `norm(permute(t, (leftind, rightind)) - U * S * V) ≈ ϵ`, where `ϵ` thus represents the truncation error.

If `leftind` and `rightind` are not specified, the current partition of left and right indices of `t` is used. In that case, less memory is allocated if one allows the data in `t` to be destroyed/overwritten, by using `tsvd!(t, trunc = notrunc(), p = 2)`.

A truncation parameter `trunc` can be specified for the new internal dimension, in which case a truncated singular value decomposition will be computed. Choices are:

  * `notrunc()`: no truncation (default);
  * `truncerr(η::Real)`: truncates such that the p-norm of the truncated singular values is   smaller than `η`;
  * `truncdim(χ::Int)`: truncates such that the equivalent total dimension of the internal   vector space is no larger than `χ`;
  * `truncspace(V)`: truncates such that the dimension of the internal vector space is   smaller than that of `V` in any sector.
  * `truncbelow(η::Real)`: truncates such that every singular value is larger then `η` ;

Truncation options can also be combined using `&`, i.e. `truncbelow(η) & truncdim(χ)` will choose the truncation space such that every singular value is larger than `η`, and the equivalent total dimension of the internal vector space is no larger than `χ`.

The method `tsvd` also returns the truncation error `ϵ`, computed as the `p` norm of the singular values that were truncated.

THe keyword `alg` can be equal to `SVD()` or `SDD()`, corresponding to the underlying LAPACK algorithm that computes the decomposition (`_gesvd` or `_gesdd`).

Orthogonality requires `InnerProductStyle(t) <: HasInnerProduct`, and `tsvd(!)` is currently only implemented for `InnerProductStyle(t) === EuclideanInnerProduct()`.
