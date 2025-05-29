```julia
ScrambleMethod <: RandomizationMethod
```

A scramble method needs at least the scrambling base `b`, the number of "bits" to use `pad` (`pad=32` is the default) and a seed `rng` (`rng = Random.GLOBAL_RNG` is the default). The scramble methods implementer are

  * `DigitalShift`.
  * `OwenScramble`: Nested Uniform Scramble which was introduced in Owen (1995).
  * `MatousekScramble`: Linear Matrix Scramble which was introduced in Matousek (1998).
