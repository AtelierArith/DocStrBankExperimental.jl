```
hybrid_fractal_2d(; kwargs...)
```

Construct a sampler that outputs a 2-dimensional hybrid multifractal noise when it is sampled from.

# Arguments

  * `seed`: An unsigned integer used to seed the random number generator for this sampler, or `nothing` for non-deterministic results.
  * `source::AbstractSampler=opensimplex2s_2d()`: A 2-dimensional sampler instance to use as the source of the fractal.
  * `octaves=4`: An integer between 1 and 32, denoting the number of octaves to apply.
  * `frequency=1.0`: The frequency of the first octave's signal.
  * `lacunarity=2.0`: A multiplier that determines how quickly the frequency increases for successive octaves.
  * `persistence=0.25`: A multiplier that determines how quickly the amplitude diminishes for successive octaves.
