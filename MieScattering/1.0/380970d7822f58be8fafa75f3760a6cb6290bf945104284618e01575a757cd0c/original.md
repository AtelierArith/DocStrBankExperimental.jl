Calculate the scattering amplitude functions for spheres. The amplitude functions have been normalized so that when integrated over all `4*π` solid angles, the integral will be `qext*pi*x^2`. The units are weird, $sr^{-0.5}$.

# Parameters

  * `m`: the complex index of refraction of the sphere
  * `x`: the size parameter of the sphere
  * `µ`: the angles, cos($θ$), to calculate scattering amplitudes
  * `norm` (optional): The normalization. Must be one of :albedo (default), :one, :four_pi, :qext,

:qsca, :bohren or :wiscombe"

  * `use_threads` (optional): Flag whether to use threads (default: true)

# Output

`S1`, `S2`: the scattering amplitudes at each angle µ [$sr^{-0.5}$]
