```
turbulence(s1::AbstractSampler; s2::AbstractSampler; kwargs...)
```

Construct a modifier sampler that displaces the input coordinates of sampler `s1` by the output of sampler `s2` with a fractional Brownian motion fractal applied to it.

Sampler `s2`'s input coordinates are randomly generated using the seed of sampler `s1`.

# Arguments

  * `frequency=1.0`: The frequency of the fractal signal to apply to sampler `s2`.
  * `roughness=3`: The number of octaves of the fractal to apply to sampler `s2`.
  * `power=1.0`: A scaling factor that is applied to the displaced result before sampling from sampler `s1`.
