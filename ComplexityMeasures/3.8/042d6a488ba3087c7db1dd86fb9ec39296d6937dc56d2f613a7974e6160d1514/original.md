```
RelativeFirstDifferenceEncoding <: Encoding
RelativeFirstDifferenceEncoding(minval::Real, maxval::Real; n = 2)
```

`RelativeFirstDifferenceEncoding` encodes a vector based on the relative position the average of the *first differences* of the vectors has with respect to a predefined minimum and maximum value (`minval` and `maxval`, respectively).

## Description

This encoding is inspired by [Azami2016](@citet)'s algorithm for amplitude-aware permutation entropy. They use a linear combination of amplitude information and first differences information of state vectors to correct probabilities. Here, however, we explicitly encode the first differences part of the correction as an a integer symbol `Λ ∈ [1, 2, …, n]`. The amplitude part of the encoding is available as the [`RelativeMeanEncoding`](@ref) encoding.

## Encoding/decoding

When used with [`encode`](@ref), an $m$-element state vector $\bf{x} = (x_1, x_2, \ldots, x_m)$ is encoded as $Λ = \dfrac{1}{m - 1}\sum_{k=2}^m |x_{k} - x_{k-1}|$. The value of $Λ$ is then normalized to lie on the interval `[0, 1]`, assuming that the minimum/maximum value any single $abs(x_k - x_{k-1})$ can take is `minval`/`maxval`, respectively. Finally, the interval `[0, 1]` is discretized into `n` discrete bins, enumerated by positive integers `1, 2, …, n`, and the number of the bin that the normalized $Λ$ falls into is returned. The smaller the mean first difference of the state vector is, the smaller the bin number is. The higher the mean first difference of the state vectors is, the higher the bin number is.

When used with [`decode`](@ref), the left-edge of the bin that the normalized $Λ$ fell into is returned.

## Performance tips

If you are encoding multiple input vectors, it is more efficient to construct a [`RelativeFirstDifferenceEncoding`](@ref) instance and re-use it:

```julia
minval, maxval = 0, 1
encoding = RelativeFirstDifferenceEncoding(minval, maxval; n = 4)
pts = [rand(3) for i = 1:1000]
[encode(encoding, x) for x in pts]
```
