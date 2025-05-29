```
zlauum(uplo::Char, n::Int, a::AbstractMatrix{T}, lda::Int, block_size::Int)
```

This function computes the product of a triangular matrix with its conjugate transpose. Specifically, it computes:

  * `U * U'` if the triangular matrix `U` is stored in the upper part of matrix `a`.
  * `L' * L` if the triangular matrix `L` is stored in the lower part of matrix `a`.

Where:

  * `U'` represents the conjugate transpose of the upper triangular matrix `U`.
  * `L'` represents the conjugate transpose of the lower triangular matrix `L`.

### Parameters:

  * `uplo`: A character (`'U'` or `'L'`) that specifies whether the triangular matrix is stored in the upper or lower part of `a`.

      * `'U'`: Indicates that the upper triangle contains the triangular matrix `U`. The result of `U * U'` will overwrite the corresponding entries in the upper triangle of matrix `a`.
      * `'L'`: Indicates that the lower triangle contains the triangular matrix `L`. The result of `L' * L` will overwrite the corresponding entries in the lower triangle of matrix `a`.
  * `n`: The order (size) of the triangular matrix. This must be a non-negative integer, representing the dimensions of the square matrix `a`, which is `n x n`.
  * `a`: The matrix where the triangular factor `U` or `L` is stored, and where the result will be stored after computation. This matrix is modified in place, meaning its contents will change as a result of the computation.
  * `lda`: The leading dimension of the array `a`. This should be at least `max(1, n)`. This parameter is important for accessing the elements of the matrix in memory correctly, particularly in scenarios where matrices may be stored in a non-contiguous fashion for performance reasons.
  * `block_size`: This specifies the block size for the blocked algorithm. A blocked algorithm processes the matrix in submatrices (or blocks), improving performance on large matrices by making better use of CPU cache and reducing memory bandwidth demands.

### Returns:

  * `info`: An integer indicating the success or failure of the function execution:

      * `0`: Indicates successful execution.
      * A negative integer indicates that an invalid argument was provided:

          * `-1`: Invalid value for `uplo`.
          * `-2`: Invalid value for `n`.
          * `-4`: Invalid value for `lda`.
