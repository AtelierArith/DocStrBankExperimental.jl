```
streamfunctionfrompv!(ψh, qh, params::TwoLayerParams, grid)
```

Invert the PV to obtain the Fourier transform of the streamfunction `ψh` for the special case of a two fluid layer configuration. In this case we have,

$$
ψ̂₁ = - [k² q̂₁ + (f₀² / g′) (q̂₁ / H₂ + q̂₂ / H₁)] / Δ ,
$$

$$
ψ̂₂ = - [k² q̂₂ + (f₀² / g′) (q̂₁ / H₂ + q̂₂ / H₁)] / Δ ,
$$

where $Δ = k² [k² + f₀² (H₁ + H₂) / (g′ H₁ H₂)]$.

(Here, the PV-streamfunction relationship is hard-coded to avoid scalar operations on the GPU.)
