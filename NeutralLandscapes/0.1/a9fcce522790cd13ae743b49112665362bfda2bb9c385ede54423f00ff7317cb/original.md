```
PerlinNoise <: NeutralLandscapeMaker

PerlinNoise(; kw...)
PerlinNoise(periods, [octaves=1, lacunarity=2, persistance=0.5, valley=:u])
```

Create a Perlin noise neutral landscape model with values ranging 0-1.

# Keywords

  * `periods::Tuple{Int,Int}=(1,1)`: the number of periods of Perlin noise across row and    column dimensions for the first octave.
  * `octaves::Int=1`: the number of octaves that will form the Perlin noise.
  * `lacunarity::Int=2` : the rate at which the frequency of periods increases for each    octive.
  * `persistance::Float64=0.5` : the rate at which the amplitude of periods decreases for each    octive.
  * `valley::Symbol=`:u`: the kind of valley bottom that will be mimicked:`:u`produces    u-shaped valleys,`:v`produces v-shaped valleys, and`:-` produces flat bottomed    valleys.

Note: This is a memory-intensive algorithm with some settings. Be careful using larger  prime numbers for `period` when also using a large array size, high lacuarity and/or many  octaves. Memory use scales with the lowest common multiple of `periods`.
