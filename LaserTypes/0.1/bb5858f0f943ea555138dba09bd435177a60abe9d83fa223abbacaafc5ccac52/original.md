```
QuasiRectangularProfile{V,T,L}
```

This envelope produces a pulse with a predominant constant part of width $Δz$ which could offer better results than the Gaussian profile in the paraxial limit (which is considered for the spatial profiles). The shape of the envelope is given by

$$
envelope(z, t) =
    \begin{cases}
    \exp\left[-\left(\frac{φ + Δt/2}{τ}\right)^2\right], & \text{for } φ ≤ \frac{Δt}{2}\\
    1\,, & \text{for } \text{otherwise}\\
    \exp\left[-\left(\frac{φ - Δt/2}{τ}\right)^2\right], & \ φ > \frac{Δt}{2}
    \end{cases}
$$

where

$$
\varphi = (t - t_0) - \frac{z - z_0}{c}\,,
$$

and

  * `c` is the speed of light
  * `τ` is the duration of the pulse (FWHM) and has the default value 18.02fs
  * `t₀` is the origin of the time axis and it is 0 by default
  * `z₀` is the initial position of the intensity peak and has the default value `-4*τ*c`
  * `Δt` is the duration of the flat part of the profile and the default value `10*τ`
