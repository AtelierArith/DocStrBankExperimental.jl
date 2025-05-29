```
bias_correction(kernel::Tophat{T},
                density::Real, m::Real, h_inv::Real,
                n_neighbours::Integer) where {T}
```

Corrects the density estimate for the kernel bias. Not implemented for [`Tophat`](@ref).
