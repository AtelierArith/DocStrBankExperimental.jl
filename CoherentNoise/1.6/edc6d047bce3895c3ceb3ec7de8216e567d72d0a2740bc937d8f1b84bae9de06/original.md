```
opensimplex_3d(; seed=nothing, smooth=false)
```

Construct a sampler that outputs 3-dimensional legacy OpenSimplex noise when it is sampled from.

# Arguments

  * `seed`: An unsigned integer used to seed the random number generator for this sampler, or `nothing` for non-deterministic results.
  * `smooth`: Specify whether to have continuous gradients. Simplex variants, even the original Simplex noise by Ken Perlin, overshoot the radial extent for the signal reconstruction kernel in order to improve the visual of the noise. Normally this is okay, especially if layering multiple octaves of the noise. However, in some applications, such as creating height or bump maps, this will produce discontinuities visually identified by jarring creases in the generated noise.

    This option changes the falloff in order to produce smooth continuous noise, however, the resulting noise may look quite different than the non-smooth option, depending on the Simplex variant.

    The default value is `false`, in order to be true to the original implementation.

# See also:

  * [`opensimplex2_3d`](@ref opensimplex2_3d)
  * [`opensimplex2s_3d`](@ref opensimplex2s_3d)
