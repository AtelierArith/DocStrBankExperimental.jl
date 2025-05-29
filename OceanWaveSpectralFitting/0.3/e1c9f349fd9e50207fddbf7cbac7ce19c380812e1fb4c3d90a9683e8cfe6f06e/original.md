```
JONSWAP{K}(α,ωₚ,γ,r)
JONSWAP{K}(x)
```

4 parameter JONSWAP model for vertical displacement.

# Type parameter

The type parameter `K` is a non-negative integer representing the ammount of aliasing to be done. This is useful as some devices have high-pass filters which limit the ammount of aliasing that will be present in a recorded series. In particular, a `JONSWAP{K}` model for a series recorded every `Δ` seconds would be appropriate for a series sampled every `Δ` seconds and filtered with a high-pass filter at `(2K-1)π/Δ`.

# Arguments

  * `α`: The scale parameter.
  * `ωₚ`: The peak angular frequency.
  * `γ`: The peak enhancement factor.
  * `r`: The tail decay index.

# Vector constructor arguments

  * `x`: Vector of parameters `[α,ωₚ,γ,r]`.

# Background

The JONSWAP spectral density function is 

$$
f(ω) = αω^{-r}\exp\left \{-\frac{r}{4}\left(\frac{|ω|}{ωₚ}\right)^{-4}\right \}γ^{δ(|ω|)}
$$

where

$$
δ(ω) = \exp\left\{-\tfrac{1}{2 (0.07+0.02\cdot\mathbb{1}_{ωₚ>|ω|})^2}\left (\tfrac{|ω|}{ωₚ}-1\right )^2\right\}.
$$
