```
Diskmargin
```

The notation follows "An Introduction to Disk Margins", Peter Seiler, Andrew Packard, and Pascal Gahinet

# Fields:

`α`: The disk margin `ω0`: The worst-case frequency `f0`: The destabilizing perturbation `f0` is a complex number with simultaneous gain and phase variation. This critical perturbation causes an instability with closed-loop pole on the imaginary axis at the critical frequency ω0  `δ0`: The uncertain element generating f0. `γmin`: The lower real-axis intercept of the disk (analogous to classical lower gain margin). `γmax`: The upper real-axis intercept of the disk (analogous to classical upper gain margin). `ϕm`: is analogous to the classical phase margin. `σ`: The skew parameter that was used to calculate the margin

Note, `γmax` and `ϕm` are in smaller than the classical gain and phase margins sicne the classical margins do not consider simultaneous perturbations in gain and phase. 

The "disk" margin becomes a half plane for `α = 2` and an inverted circle for `α > 2`. In this case, the upper gain margin is infinite. See the paper for more details, in particular figure 6.
