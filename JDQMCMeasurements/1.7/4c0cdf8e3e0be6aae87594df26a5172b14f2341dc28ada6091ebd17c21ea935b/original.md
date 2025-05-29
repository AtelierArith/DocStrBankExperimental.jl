```
cubic_spline_τ_to_ωn!(
    Cn::AbstractVector{Complex{E}},
    Cτ::AbstractVector{T},
    β::E, Δτ::E;
    spline_type::String = "C2",
    M1::T = NaN,
    M2::T = NaN
) where {E<:AbstractFloat, T<:Number}
```

Calculate the Matsubara frequency representation

$$
\begin{align*}
C(\mathrm{i}\omega_n) = \int_0^\beta d\tau \ e^{\mathrm{i}\omega_n\tau} C(\tau)
\end{align*}
$$

of an imaginary-time correlation function $C(\tau)$ defined on a regular grid of $L + 1$ imaginary-time points $\tau \in \{ 0, \Delta\tau, 2\Delta\tau, \ldots, (\beta-\Delta\tau), \beta \}.$ This is done by fitting a cubic spline through the $C(\tau)$ points, and then transforming the spline. Here, the Matsubara correlations $C(\mathrm{i}\omega_n)$ are written to the vector `Cn`, and the imaginary-time correlations $C(\tau)$ are stored in the vector `Cτ`. It is assumed that `C[1]` and `C[end]` correspond to $C(\tau = 0)$ and $C(\tau = \beta)$ respectively. It is also assumed that $L = \beta/\Delta\tau.$

Note that the length of the vector `Cn` determines whether the correlation function is assumed to be fermionic or bosonic.

For fermoinic correlation functions, `mod(M, 2L) == 0`, where `M = length(Cn)` and `L = length(Cτ) - 1`. Put another way, it must be that `length(Cn) == 2*n*(length(Cτ)-1)` for some positive integer `n ≥ 1`. In this case the vector `Cn` contains Matsubara frequency correlation $C(\mathrm{i}\omega_n)$ for $n \in [-N, (N-1)]$, where `N = M÷2` and $\omega_n = (2n+1)\pi/\beta$.

For bosonic correlation functions `mod(M+1, 2L) == 0`, where `M = length(Cn)` and `L = length(Cτ) - 1`. Put another way, it must be that `length(Cn) == 2*n*(length(Cτ)-1) - 1` for some positive integer `n ≥ 1`. In this case the vector `Cn` contains Matsubara frequency correlation $C(\mathrm{i}\omega_n)$ for $n \in [-N, N]$, where `N = (M-1)÷2` and $\omega_n = 2n\pi/\beta$.

The `spline_type` argument can be set to `"C2"`, `"akima"`, or `"makima"` to specify the type of spline to use. The default argument (and best for most cases) is `"C2"`, which refers to a C2 cubic spline with continuous first and second derivatives. In this case, boundary conditions are imposed such that the second derivative of the spline at `τ=0` and `τ=β` are set equal to the second derivative as calculated using a second-order forward and backward finite difference respectively.

The `M1` and `M2` arguments can be used to specify the first and second moments of the spectral function if known. By default the are set to `NaN`, which results in them being calculated internally based on the imaginary-time correlation function data points and corresponding spline fit.
