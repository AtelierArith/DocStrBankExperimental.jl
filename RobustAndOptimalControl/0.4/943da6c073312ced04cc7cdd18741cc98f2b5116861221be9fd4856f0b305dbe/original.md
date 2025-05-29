```
neglected_lag(τmax)
```

Return a multiplicative weight to represent the uncertainty coming from neglecting the dynamics `1/(s*τ + 1)` where `τ ≤ τmax`. "Multivariable Feedback Control: Analysis and Design" Ch 7.4.5

See also [`gain_and_delay_uncertainty`](@ref) and [`neglected_delay`](@ref).

# Example:

```julia
a = 10
P = ss([0 a; -a 0], I(2), [1 a; -a 1], 0) # Plant
W0 = neglected_lag(0.05) |> ss # Weight
W = I(2) + W0*I(2) * uss([δc(), δc()]) # Create a diagonal real uncertainty weighted in frequency by W0
Ps = P*W # Uncertain plant
Psamples = rand(Ps, 100) # Sample the uncertain plant for plotting
w = exp10.(LinRange(-1, 3, 300)) # Frequency vector
sigmaplot(Psamples, w)
```
