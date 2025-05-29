```
RelativeMeanEncoding <: Encoding
RelativeMeanEncoding(minval::Real, maxval::Real; n = 2)
```

`RelativeMeanEncoding` encodes a vector based on the relative position the mean of the vector has with respect to a predefined minimum and maximum value (`minval` and `maxval`, respectively).

## Description

This encoding is inspired by [Azami2016](@citet)'s algorithm for amplitude-aware permutation entropy. They use a linear combination of amplitude information and first differences information of state vectors to correct probabilities. Here, however, we explicitly encode the amplitude-part of the correction as an a integer symbol `Λ ∈ [1, 2, …, n]`. The first-difference part of the encoding is available as the [`RelativeFirstDifferenceEncoding`](@ref) encoding.

## Encoding/decoding

When used with [`encode`](@ref), an $m$-element state vector $\bf{x} = (x_1, x_2, \ldots, x_m)$ is encoded as $Λ = \dfrac{1}{N}\sum_{i=1}^m abs(x_i)$. The value of $Λ$ is then normalized to lie on the interval `[0, 1]`, assuming that the minimum/maximum value any single element $x_i$ can take is `minval`/`maxval`, respectively. Finally, the interval `[0, 1]` is discretized into `n` discrete bins, enumerated by positive integers `1, 2, …, n`, and the number of the bin that the normalized $Λ$ falls into is returned.

When used with [`decode`](@ref), the left-edge of the bin that the normalized $Λ$ fell into is returned.
