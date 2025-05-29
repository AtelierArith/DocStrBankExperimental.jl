```
doubleeuler(sys::AbstractStateSpace{<:Continuous}, Ts)
```

Discretize `sys` with a second-order approximation to the exponential map (Forward Euler is a first-order approximation). This is useful if the symbolic expressions for the true ZoH-discretization becomes too complicated. A second-order approximation is in some cases close to the true ZoH-discretization, but requires a well-balanced state-space realization. See also [`pade_zoh`](@ref).

# Example

```julia
w = 2pi .* exp10.(LinRange(-1, log10(25), 400))
sys = ssrand(1,1,4)
bodeplot(sys, w, lab="cont")
bodeplot!(c2d(sys, 0.001, :fwdeuler), w, label="fwdeuler")
bodeplot!(doubleeuler(sys, 0.001), w, label="double euler")
```
