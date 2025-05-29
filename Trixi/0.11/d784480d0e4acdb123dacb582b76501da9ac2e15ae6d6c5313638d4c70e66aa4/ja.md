```
source_terms_lorentz(u, x, t, equations::AbstractIdealGlmMhdMultiIonEquations)
```

ローレンツ力によるソース項は、複数のイオン種を持つプラズマに対するものです。これらのソース項は、マルチイオンGLM-MHD方程式の基本的で切り離せない部分であり、単一種プラズマでは消失します。特に、[`IdealGlmMhdMultiIonEquations2D`](@ref)および[`IdealGlmMhdMultiIonEquations3D`](@ref)のすべてのシミュレーションに使用する必要があります。
