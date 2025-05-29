```
CosSquarePulse(mom::M,pulse_length::T) where {M<:QEDbase.AbstractFourMomentum,T<:Real}
```

Concrete implementation of an `AbstractPulsedPlaneWaveField` for cos-square pulses.

!!! note "Pulse shape"
    The pulse envelope of a cos-square pulse is defined as 

    $$
    g(\phi) = \cos^2(\frac{\pi\phi}{2\Delta\phi})
    $$

    for $\phi\in (-\Delta\phi,\Delta\phi)$, where $\Delta\phi$ denotes the `pulse_length`, and zero otherwise.

