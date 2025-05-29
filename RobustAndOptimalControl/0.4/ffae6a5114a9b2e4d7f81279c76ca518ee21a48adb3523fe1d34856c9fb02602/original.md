```
gain_and_delay_uncertainty(kmin, kmax, Lmax)
```

Return a multiplicative weight to represent the uncertainty coming from neglecting the dynamics `k*exp(-s*L)` where `k ∈ [kmin, kmax]` and `L ≤ Lmax`. This weight is slightly optimistic, an expression for a more exact weight appears in eq (7.27), "Multivariable Feedback Control: Analysis and Design"

See also [`neglected_lag`](@ref) and [`neglected_delay`](@ref).

# Example:

```julia
a = 10
P = ss([0 a; -a 0], I(2), [1 a; -a 1], 0) # Plant
W0 = gain_and_delay_uncertainty(0.5, 2, 0.005) |> ss # Weight
W = I(2) + W0*I(2) * uss([δc(), δc()]) # Create a diagonal real uncertainty weighted in frequency by W0
Ps = P*W # Uncertain plant
Psamples = rand(Ps, 500) # Sample the uncertain plant for plotting
w = exp10.(LinRange(-1, 3, 300)) # Frequency vector
bodeplot(Psamples, w)
```
