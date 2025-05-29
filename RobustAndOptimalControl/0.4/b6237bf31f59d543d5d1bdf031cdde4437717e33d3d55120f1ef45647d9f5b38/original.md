```
diskmargin(L, σ = 0)
diskmargin(L, σ::Real, ω)
```

Calculate the disk margin of LTI system `L`. `L` is supposed to be a loop-transfer function, i.e., it should be square. If `L = PC` the disk margin for output perturbations is computed, whereas if `L = CP`, input perturbations are considered. If the method `diskmargin(P, C, args...)` is used, both are computed. Note, if `L` is MIMO, a simultaneous margin is computed, see [`loop_diskmargin`](@ref) for single loop margins of MIMO systems.

The implementation and notation follows ["An Introduction to Disk Margins", Peter Seiler, Andrew Packard, and Pascal Gahinet](https://arxiv.org/abs/2003.04771).

The margins are aviable as fields of the returned objects, see [`Diskmargin`](@ref).

# Arguments:

  * `L`: A loop-transfer function.
  * `σ`: If little is known about the distribution of gain variations then σ = 0 is a reasonable choice as it allows for a gain increase or decrease by the same relative amount. *The choice σ < 0* is justified if the gain can decrease by a larger factor than it can increase. Similarly, *the choice σ > 0* is justified when the gain can increase by a larger factor than it can decrease. *If σ = −1* then the disk margin condition is αmax = inv(MT). This margin is related to the robust stability condition for models with multiplicative uncertainty of the form P (1 + δ). If σ = +1 then the disk margin condition is αmax = inv(MS)
  * `kwargs`: Are sent to the [`hinfnorm`](@ref) calculation
  * `ω`: If a vector of frequencies is supplied, the frequency-dependent disk margin will be computed, see example below.

# Example:

```
L = tf(25, [1,10,10,10])
dm = diskmargin(L, 0)
plot(dm) # Plot the disk margin to illustrate maximum allowed simultaneous gain and phase variations.

nyquistplot(L)
plot!(dm, nyquist=true) # plot a nyquist exclusion disk. The Nyquist curve will be tangent to this disk at `dm.ω0`
nyquistplot!(dm.f0*L) # If we perturb the system with the worst-case perturbation `f0`, the curve will pass through the critical point -1.

## Frequency-dependent margin
w = exp10.(LinRange(-2, 2, 500))
dms = diskmargin(L, 0, w)
plot(dms; lower=true, phase=true)
```

# Example: relation to Ms and Mt

```
Ms, wMs = hinfnorm(input_sensitivity(P, C)) # Input Ms
dm = diskmargin(C*P, 1) # Input diskmargin, skew = +1
isapprox(Ms/(Ms-1), dm.gainmargin[2], rtol=1e-2) # Guaranteed gain margin based on Ms
isapprox(inv(Ms), dm.margin, rtol=1e-2)
isapprox(dm.ω0, wMs, rtol=1e-1)


Mt, wMt = hinfnorm(input_comp_sensitivity(P, C)) # Input Mt
dm = diskmargin(C*P, -1) # Input diskmargin, skew = -1
isapprox(inv(Mt), dm.margin, rtol=1e-2)
isapprox(dm.ω0, wMt, rtol=1e-1)
```

See also [`ncfmargin`](@ref) and [`loop_diskmargin`](@ref).
