```
pvfromstreamfunction!(qh, ψh, params::TwoLayerParams, grid)
```

Obtain the Fourier transform of the PV from the streamfunction `ψh` for the special case of a two fluid layer configuration. In this case we have,

$$
q̂₁ = - k² ψ̂₁ + f₀² / (g′ H₁) (ψ̂₂ - ψ̂₁) ,
$$

$$
q̂₂ = - k² ψ̂₂ + f₀² / (g′ H₂) (ψ̂₁ - ψ̂₂) .
$$

(Here, the PV-streamfunction relationship is hard-coded to avoid scalar operations on the GPU.)
