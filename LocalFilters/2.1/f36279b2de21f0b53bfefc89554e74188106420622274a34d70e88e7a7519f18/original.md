LocalFilters.centered_offset(len)

yields the index offset along a centered dimension of length `len`. That is, `-div(Int(len)+2,2)`. For even dimension lengths, this amounts to using the same conventions as in `fftshift`.

See [`LocalFilters.kernel_range`](@ref) and [`LocalFilters.centered`](@ref).
