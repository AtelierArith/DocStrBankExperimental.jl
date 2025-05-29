Calculate the backscattering cross-section (sigma_bs) of a scatterer using the (S)DWBA. This is the absolute square of the form function.

#### Parameters

  * `s` : Scatterer object.
  * `k` : Acoustic wavenumber vector.  Its magnitude is 2 * pi * f / c (where

f is the frequency and c is the sound speed) and it points in the direction of propagation.  For downward-propagating sound waves, it is [0, 0, -2pi * f / c].

  * `phase_sd` : Standard deviation of the phase variability for each segment (in radians).

Defaults to 0.0, that is, an ordinary deterministic DWBA.  If > 0, the return value will be stochastic (i.e., the SDWBA).
