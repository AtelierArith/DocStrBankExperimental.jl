```
up_down_instability(pnsystem)
```

Compute the range of frequencies over which the system is unstable to increasing precession.

The returned value is a pair of dimensionless frequencies giving the lower and upper frequencies between which we can expect instability.  If there is no instability expected, the returned pair is just $(1/M, 1/M)$ — where $M$ is the total mass of the system, and $1/M$ is the upper limit of physically reasonable frequencies.

For compact binaries in which the spins are either aligned or anti-aligned with the orbital angular velocity, we do not expect any precession effects — simply by symmetry.  However, if the spin of the higher-mass object is aligned with the orbital angular velocity and the spin of the lower-mass object is anti-aligned, the binary is unstable to precession — meaning that any minuscule misalignment can grow rapidly into significant precession.  This was first reported by [Gerosa et al. (2015)](http://arxiv.org/abs/1506.09116), and the range over which the system is unstable is given by Eq. (2) of that reference.  We use the lowest-order approximation to convert binary separation to frequency.  The result is also "clamped" between $0$ and $1/M$, because sometimes the PN approximations involved break down and return values outside of those physically plausible limits.

Note that Gerosa et al. use the convention that $q = M_2/M_1$ — which is opposite to the convention used in [this package](@ref q); which we account for internally in this function. They also assume that $M_1 \geq M_2$, which we deal with by automatically swapping the relevant quantities.  Neither of these requires any adjustment by users of this function.
