```
icwt(res::AbstractArray, cWav::CWT, inverseStyle::InverseType=PenroseDelta())
```

Compute the inverse wavelet transform using one of three dual frames. The default uses delta functions with weights chosen via a least squares method, the `PenroseDelta()` below. This is chosen as a default because the Morlet wavelets tend to fail catastrophically using the canonical dual frame (the `dualFrames()` type).

```
icwt(res::AbstractArray, cWav::CWT, inverseStyle::PenroseDelta)
```

Return the inverse continuous wavelet transform, computed using the simple dual frame $β_jδ_{ji}$, where $β_j$ is chosen to solve the least squares problem $\|Ŵβ-1\|_2^2$, where $Ŵ$ is the Fourier domain representation of the `cWav` wavelets. In both this case and `NaiveDelta()`, the fourier transform of $δ$ is the constant function, thus this least squares problem.

```
icwt(res::AbstractArray, cWav::CWT, inverseStyle::NaiveDelta)
```

Return the inverse continuous wavelet transform, computed using the simple dual frame $β_jδ_{ji}$, where $β_j$ is chosen to negate the scale factor $(^1/_s)^{^1/_p}$. Generally less accurate than choosing the weights using `PenroseDelta`. This is the method discussed in Torrence and Compo.

```
icwt(res::AbstractArray, cWav::CWT, inverseStyle::dualFrames)
```

Return the inverse continuous wavelet transform, computed using the canonical dual frame $\tilde{\widehat{ψ}} = \frac{ψ̂_n(ω)}{∑_n\|ψ̂_n(ω)\|^2}$. The algorithm is to compute the cwt again, but using the canonical dual frame; consequentially, it is the most computationally intensive of the three algorithms, and typically the best behaved. Will be numerically unstable if the high frequencies of all of the wavelets are too small however, and tends to fail spectacularly in this case.
