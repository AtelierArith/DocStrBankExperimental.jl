```
svd(A::ITensor, inds::Index...; <keyword arguments>)
```

Singular value decomposition (SVD) of an ITensor `A`, computed by treating the "left indices" provided collectively as a row index, and the remaining "right indices" as a column index (matricization of a tensor).

The first three return arguments are `U`, `S`, and `V`, such that `A ≈ U * S * V`.

Whether or not the SVD performs a trunction depends on the keyword arguments provided.

If the left or right set of indices are empty, all input indices are put on `V` or `U` respectively. To specify an empty set of left indices, you must explicitly use `svd(A, ())` (`svd(A)` is currently undefined).

# Examples

Computing the SVD of an order-three ITensor, such that the indices i and k end up on U and j ends up on V

```
i = Index(2)
j = Index(5)
k = Index(2)
A = random_itensor(i, j, k)
U, S, V = svd(A, i, k);
@show norm(A - U * S * V) <= 10 * eps() * norm(A)
```

The following code will truncate the last 2 singular values, since the total number of singular values is 4. The norm of the difference with the original tensor will be the sqrt root of the sum of the squares of the singular values that get truncated.

```
trunc, Strunc, Vtrunc = svd(A, i, k; maxdim=2);
@show norm(A - Utrunc * Strunc * Vtrunc) ≈ sqrt(S[3, 3]^2 + S[4, 4]^2)
```

Alternatively we can specify that we want to truncate the weights of the singular values up to a certain cutoff, so the total error will be no larger than the cutoff.

```
Utrunc2, Strunc2, Vtrunc2 = svd(A, i, k; cutoff=1e-10);
@show norm(A - Utrunc2 * Strunc2 * Vtrunc2) <= 1e-10
```

# Keywords

  * `maxdim::Int`: the maximum number of singular values to keep.
  * `mindim::Int`: the minimum number of singular values to keep.
  * `cutoff::Float64`: set the desired truncation error of the SVD,  by default defined as the sum of the squares of the smallest singular values.
  * `lefttags::String = "Link,u"`: set the tags of the Index shared by `U` and `S`.
  * `righttags::String = "Link,v"`: set the tags of the Index shared by `S` and `V`.
  * `alg::String = "divide_and_conquer"`. Options:
  * `"divide_and_conquer"` - A divide-and-conquer algorithm.    LAPACK's gesdd. Fast, but may lead to some innacurate singular values    for very ill-conditioned matrices. Also may sometimes fail to converge,    leading to errors (in which case "qr_iteration" or "recursive" can be tried).

      * `"qr_iteration"` - Typically slower but more accurate for very  ill-conditioned matrices compared to `"divide_and_conquer"`.  LAPACK's gesvd.
      * `"recursive"` - ITensor's custom svd. Very reliable, but may be slow if  high precision is needed. To get an `svd` of a matrix `A`, an  eigendecomposition of $A^{\dagger} A$ is used to compute `U` and then  a `qr` of $A^{\dagger} U$ is used to compute `V`. This is performed  recursively to compute small singular values.
  * `use_absolute_cutoff::Bool = false`: set if all probability weights below  the `cutoff` value should be discarded, rather than the sum of discarded  weights.
  * `use_relative_cutoff::Bool = true`: set if the singular values should be  normalized for the sake of truncation.
  * `min_blockdim::Int = 0`: for SVD of block-sparse or QN ITensors, require  that the number of singular values kept be greater than or equal to  this value when possible

See also: [`factorize`](@ref), [`eigen`](@ref)
