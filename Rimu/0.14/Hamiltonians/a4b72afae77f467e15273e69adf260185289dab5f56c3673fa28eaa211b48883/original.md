```
G2MomCorrelator(d::Int) <: AbstractOperator{ComplexF64}
```

Two-body correlation operator representing the density-density correlation at distance `d`. It returns a `Complex` value.

Correlation within a single component:

$$
\hat{G}^{(2)}(d) = \frac{1}{M}\sum_{spqr=1}^M e^{-id(p-q)2π/M} a^†_{s} a^†_{p}  a_q a_r δ_{s+p,q+r}
$$

The diagonal element, where `(p-q)=0`, is

$$
\frac{1}{M}\sum_{k,p=1}^M a^†_{k} b^†_{p}  b_p a_k .
$$

# Arguments

  * `d::Integer`: the distance between two particles.

# See also

  * [`Rimu.G2RealCorrelator`](@ref)
  * [`Rimu.G2RealSpace`](@ref)
  * [`Rimu.AbstractOperator`](@ref)
  * [`Rimu.AllOverlaps`](@ref)
