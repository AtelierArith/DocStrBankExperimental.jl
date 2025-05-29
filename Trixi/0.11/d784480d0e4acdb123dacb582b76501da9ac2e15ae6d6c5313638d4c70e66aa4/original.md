```
source_terms_lorentz(u, x, t, equations::AbstractIdealGlmMhdMultiIonEquations)
```

Source terms due to the Lorentz' force for plasmas with more than one ion species. These source  terms are a fundamental, inseparable part of the multi-ion GLM-MHD equations, and vanish for  a single-species plasma. In particular, they have to be used for every simulation of [`IdealGlmMhdMultiIonEquations2D`](@ref) and [`IdealGlmMhdMultiIonEquations3D`](@ref).
