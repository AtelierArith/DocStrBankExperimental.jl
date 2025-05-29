```
spectral_moment(order::Int, m::S, r_ps::T, fas::FourierParameters, sdof::Oscillator; nodes::Int=31, control_freqs::Vector{Float64}=[1e-3, 1e-1, 1.0, 10.0, 100.0, 300.0] ) where {S<:Real,T<:Real}
```

Compute spectral moment of a specified order.

Evaluates the expression:

$$
	m_k = 2\int_{0}^{\infty} \left(2\pi f\right)^k |H(f;f_n,\zeta_n)|^2 |A(f)|^2 df
$$

where $k$ is the order of the moment.

Integration is performed using Gauss-Legendre integration using `nodes` nodes and weights. The integration domain is partitioned over the `control_freqs` as well as two inserted frequencies at `f_n/1.5` and `f_n*1.5` in order to ensure good approximation of the integral around the `sdof` resonant frequency.

See also: [`spectral_moments`](@ref)
