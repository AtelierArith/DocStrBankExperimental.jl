```
susceptibility!(χ::AbstractArray{T}, S::AbstractArray{T}, Δτ::E, dim::Int) where {T<:Number, E<:AbstractFloat}
```

Calculate the susceptibilities

$$
\chi_\mathbf{n} = \int_0^\beta S_\mathbf{n}(\tau) d\tau,
$$

where the $\chi_\mathbf{n}$ susceptibilities are written to `χ`, and `S` contains the $S_\mathbf{n}(\tau)$ correlations that need to be integrated over. The parameter `Δτ` is the discretization in imaginary time $\tau,$ and is the step size used in Simpson's method to numerically evaluate the integral over imaginary time. The argument `dim` specifies which dimension of `S` corresponds to imaginary time, and needs to be integrated over. Accordingly,

```julia
ndim(χ)+1 == ndim(S)
```

and

```julia
size(χ) == size(selectdim(S, dim, 1))
```

must both be true.
