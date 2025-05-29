```
SecondaryLimbDark(primary::AbstractLimbDark,
                  secondary::AbstractLimbDark; 
                  brightness_ratio=1)
SecondaryLimbDark(u_p::AbstractVector, u_s=u_p; kwargs...)
```

Compose two limb darkening laws together to add a secondary eclipse. If vectors of coefficients are provided, laws will automatically be constructed using [`PolynomialLimbDark`](@ref). The surface brightness ratio is given in terms of the host; e.g., if the companion is half as bright as the host, the ratio would be 0.5.

!!! note "Interface"
    [`SecondaryLimbDark`](@ref) only works with an orbit, since the companion's reference frame needs to be calculated. This means you can't call it using an impact parameter like `ld(b, r)` directly.


# Mathematical form

$$
f(t, r) = \frac{2f_p(t, r) + \eta r^2 f_s(t', r')}{1 + f_p(t, r) + \eta r^2 f_s(t', r')}
$$

where $f_p$ is to the primary flux, $f_s$ is to the secondary flux, and $\eta$ is the surface brightness ratio. $t'$ and $r'$ correspond to the time and radius ratio from the companion's reference frame.

# Examples

```jldoctest second
using Orbits
# equal size and limb darkening
r = 1.0
u = [0.4, 0.26]
# companion is 1/10 as bright
brightness_ratio = 0.1
ld = SecondaryLimbDark(u; brightness_ratio)
orbit = SimpleOrbit(period=2, duration=0.5)
fp = ld(orbit, 0, r) # primary egress
fs = ld(orbit, 1, r) # secondary egress

fp ≈ brightness_ratio * fs

# output
true
```
