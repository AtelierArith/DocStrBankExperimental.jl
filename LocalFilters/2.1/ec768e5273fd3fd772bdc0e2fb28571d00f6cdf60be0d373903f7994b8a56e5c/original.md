LocalFilters.centered(A) -> B

yields an abstract array `B` sharing the entries of array `A` but with offsets on indices so that the axes of `B` are *centered* (for even dimension lengths, the same conventions as in `fftshift` are used).

This *public* method is purposely not exported because it could introduce some confusions. For example `OffsetArrays.centered` is similar but has a slightly different semantic.

See also [`LocalFilters.kernel_range`](@ref), [`LocalFilters.centered_offset`](@ref).
