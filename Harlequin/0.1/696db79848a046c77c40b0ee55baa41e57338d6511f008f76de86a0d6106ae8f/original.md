```
mutable struct Observation{T <: Real}
```

An *observation* is a sequence of time-ordered data (TOD) that has been acquired by some detector. It implements the following fields:

  * `time`: an array of `N` elements, representing the time of the sample. Being defined as an `AbstractArray`, a range (e.g., `0.0:0.1:3600.0`) can be used to save memory
  * `pixidx`: an array of `N` elements, each being a pixel index in a map. In no way the Healpix pixelization scheme is enforced; in fact, the map must not even be spherical.
  * `psi_angle`: an array of `N` elements, each containing the orientation of the polarization angle with respect to some fixed reference system (e.g., the Ecliptic plane). The angles must be in **radians**.
  * `tod`: an array of `N` elements, containing the actual data measured by the instrument and already calibrated to some physical units (e.g., K_CMB)
  * `sigma_squared`: an array of `N` elements, containing the squared RMS of each sample. To save memory, you should usually use a `RunLengthArray` here.
  * `flagged`: a Boolean array of `N` elements, telling whether the sample should be discarded (`true`) or not (`false`) during the map-making process.
  * `name`: a string representing the detector. This is used only for debugging purposes.

To create an observation, the constructor takes *keyword arguments* instead of parameters; in this way, the code should be more readable. Also, sensible defaults will be provided for the missing fields:

```julia
# We do not specify "sigma_squared" nor "flagged", so they will be
# initialized to a vector of ones and a vector of `false`
obs = Observation{Float64}(
    time = 0.0:0.1:3600.0,
    pixidx = 1:3601,
    psi_angle = zeros(3601),
    tod = randn(3601),
)
```
