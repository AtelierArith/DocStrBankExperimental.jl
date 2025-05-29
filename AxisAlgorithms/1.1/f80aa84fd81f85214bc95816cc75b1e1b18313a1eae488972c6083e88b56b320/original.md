`A_mul_B_md!(dest, M, src, dim)` computes `M*x` for slices `x` of `src` along dimension `dim`, storing the result in `dest`. `M` must be an `AbstractMatrix`. This uses an in-place naive algorithm.
