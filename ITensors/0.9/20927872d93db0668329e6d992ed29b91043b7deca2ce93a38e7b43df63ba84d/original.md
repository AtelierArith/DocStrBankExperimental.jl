```
factorize(A::ITensor, Linds::Index...; <keyword arguments>)
```

Perform a factorization of `A` into ITensors `L` and `R` such that `A ≈ L * R`.

# Arguments

  * `ortho::String = "left"`: Choose orthogonality  properties of the factorization.

      * `"left"`: the left factor `L` is an orthogonal basis  such that `L * dag(prime(L, commonind(L,R))) ≈ I`.
      * `"right"`: the right factor `R` forms an orthogonal basis.
      * `"none"`, neither of the factors form an orthogonal basis,   and in general are made as symmetrically as possible   (depending on the decomposition used).
  * `which_decomp::Union{String, Nothing} = nothing`: choose what kind  of decomposition is used.

      * `nothing`: choose the decomposition automatically based on  the other arguments. For example, when `nothing` is chosen and  `ortho = "left"` or `"right"`, and a cutoff is provided, `svd` or  `eigen` is used depending on the provided cutoff (`eigen` is only  used when the cutoff is greater than `1e-12`, since it has a lower  precision). When no truncation is requested `qr` is used for dense  ITensors and `svd` for block-sparse ITensors (in the future `qr`  will be used also for block-sparse ITensors in this case).
      * `"svd"`: `L = U` and `R = S * V` for `ortho = "left"`, `L = U * S`  and `R = V` for `ortho = "right"`, and `L = U * sqrt.(S)` and  `R = sqrt.(S) * V` for `ortho = "none"`. To control which `svd`  algorithm is choose, use the `svd_alg` keyword argument. See the  documentation for `svd` for the supported algorithms, which are the  same as those accepted by the `alg` keyword argument.
      * `"eigen"`: `L = U` and $R = U^{\dagger} A$ where `U` is determined  from the eigendecompositon $A A^{\dagger} = U D U^{\dagger}$ for  `ortho = "left"` (and vice versa for `ortho = "right"`). `"eigen"` is  not supported for `ortho = "none"`.
      * `"qr"`: `L=Q` and `R` an upper-triangular matrix when  `ortho = "left"`, and `R = Q` and `L` a lower-triangular matrix  when `ortho = "right"` (currently supported for dense ITensors only). In the future, other decompositions like QR (for block-sparse ITensors), polar, cholesky, LU, etc. are expected to be supported.

For truncation arguments, see: [`svd`](@ref)
