```
GaussProfile{V,T,L}
```

This envelope provides a finite duration for the laser pulse and thus can provide a more realistic description of an actual laser pulse.

$$
envelope(z, t) = \exp\left[-\left(\frac{φ}{τ}\right)^2\right],
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
