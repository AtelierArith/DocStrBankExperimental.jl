```
GaussianPulse(mom::M,pulse_length::T) where {M<:QEDbase.AbstractFourMomentum,T<:Real}
```

Concrete implementation of an `AbstractPulsedPlaneWaveField` for Gaussian pulses.

Propagates along the direction given by the space-like components of the reference momentum vector k*mu = (omega/speed*of*light, k*x, k*y, k*z), and omega = 2*pi*speed*of*light/wavelength.

The time-like coordinate omega/speed*of*ligth of k_mu defines the field's oscillation frequency.

In order to fulfill the vacuum dispersion relation, k_mu*k^mu=0 is required.

!!! note "Pulse shape"
    The longitudinal envelope of a Gaussian pulse is defined as

    $$
    g(\phi) = \exp(-\frac{\phi^2}{2\Delta\phi^2})
    $$

    for $\phi\in (-\infty, \infty) and $\Delta\phi`$ denotes the `pulse_length`.

    There is no envelope in the transverse directions.

