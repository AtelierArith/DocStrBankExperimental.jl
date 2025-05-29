```
betaU_Yukawa(amplitude::β_num, inv_screening_length::β_num, k::β_num) where {β_num<:AbstractFloat}
```

Auxiliary function to compute the Fourier Transform of a Yukawa potential, multiplied by β = 1/(k*B T*abs). The result is β * u*Yukawa*tilde(k).

The assumed dimensionless Yukawa potential in real space is u(r/σ) = (Amplitude) * exp(-z*(r/σ - 1)) / (r/σ) for r/σ >= 1. The Fourier transform can take various forms depending on the precise definition and normalization. The formula used here (from user) is: βu_tilde(k) = Factor * Amplitude * (k*cos(k) + z*sin(k)) / (k*(k² + z²)) where k is qσ, z is inv*screening*length, and Factor is 4π. The small k expansion is: βu_tilde(k) ≈ Factor * Amplitude * ( (1/z) + 1 - (z²+9z+6)/(6z²) * k² )

Note: There's a discrepancy in the k -> 0 limit between the main formula and the small-k expansion provided in the original code. The main formula for k->0 gives (1+z)/z², while the expansion gives (1+z)/z. This implementation uses the formulas as provided.

# Arguments

  * `amplitude::β_num`: Effective amplitude of the Yukawa potential (often includes β, e.g., βε).
  * `inv_screening_length::β_num`: Dimensionless inverse screening length (z).
  * `k::β_num`: Dimensionless wave vector (k = q*σ).

# Returns

  * `β_num`: The value of β * u*Yukawa*tilde(k).

# References

[1] Yukawa, H. (1935). "On the interaction of elementary particles". Proc. Phys.-Math. Soc. Jpn. 17: 48.     (Note: Specific forms for liquids often derive from this but might differ.)
