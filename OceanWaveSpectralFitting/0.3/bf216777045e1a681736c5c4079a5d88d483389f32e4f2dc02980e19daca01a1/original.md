```
JS_BWG_HNE{K}(α,ωₚ,γ,r,ϕₘ,β,ν,σₗ,σᵣ)
JS_BWG_HNE{K}(x)
```

9 parameter model for vertical, northward and eastward displacement of a partical in waves with JONSWAP marginal spectra and bimodal wrapped Gaussian spreading.

# Type parameter

The type parameter `K` is a non-negative integer representing the ammount of aliasing to be done. This is useful as some devices have high-pass filters which limit the ammount of aliasing that will be present in a recorded series. In particular, a `JS_BWG_HNE{K}` model for a series recorded every `Δ` seconds would be appropriate for a series sampled every `Δ` seconds and filtered with a high-pass filter at `(2K-1)π/Δ`.

# Arguments

  * `α`: The scale parameter.
  * `ωₚ`: The peak angular frequency.
  * `γ`: The peak enhancement factor.
  * `r`: The tail decay index.
  * `ϕₘ`: The mean direction.
  * `β`: The limiting peak separation.
  * `ν`: The peak separation shape.
  * `σₗ`: The limiting angular width.
  * `σᵣ`: The angular width shape.

# Vector constructor arguments

  * `x`: Vector of parameters `[α,ωₚ,γ,r,ϕₘ,β,ν,σₗ,σᵣ]`.

# Background

The model is a transformation of a model for the frequency-direction spectra of a wave process. Such a frequency-direction spectra, denoted $f(ω,ϕ)$ is typically decomposed by writing:

$$
f(ω,ϕ) = f(ω)D(ω,ϕ)
$$

where $f(ω)$ is the marginal spectral density function and $D(ω,ϕ)$ is the spreading function. This model uses a JONSWAP marginal sdf and a bimodal wrapped Gaussian spreading function. The JONSWAP spectral density function is 

$$
f(ω) = αω^{-r}\exp\left \{-\frac{r}{4}\left(\frac{|ω|}{ωₚ}\right)^{-4}\right \}γ^{δ(|ω|)}
$$

where

$$
δ(ω) = \exp\left\{-\tfrac{1}{2 (0.07+0.02\cdot\mathbb{1}_{ωₚ>|ω|})^2}\left (\tfrac{|ω|}{ωₚ}-1\right )^2\right\}.
$$

The bimodal wrapped Gaussian spreading function is 

$$
D(ω,ϕ) = \frac{1}{2σ(ω)\sqrt{2π}}\sum\limits_{k=-∞}^{∞} \sum\limits_{i=1}^{2} \exp\left\{-\frac{1}{2}\left(\frac{ϕ-ϕ_{mi}(ω)-2\pi k}{σ(ω)}\right)^2\right\}
$$

where

$$
\begin{align*}
    ϕ_{m1}(ω) &= ϕ_m + β \exp\{-ν \min(ω_p/|ω|,1)\}/2 \\
    ϕ_{m2}(ω) &= ϕ_m - β \exp\{-ν \min(ω_p/|ω|,1)\}/2 \\
    σ(ω) &= σ_l - \frac{σ_r}{3}\left\{ 4\left(\frac{ω_p}{|ω|}\right)^2 - \left(\frac{ω_p}{|ω|}\right)^8 \right\}
\end{align*}
$$
