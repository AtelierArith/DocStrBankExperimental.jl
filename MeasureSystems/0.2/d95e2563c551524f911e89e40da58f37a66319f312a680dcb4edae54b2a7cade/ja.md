```Julia
solidangle : [A²], [𝟙], [𝟙], [𝟙], [𝟙]
solidangle(U::UnitSystem,S::UnitSystem) = angle(U,S)^2
solidangle(v::Real,U::UnitSystem,S::UnitSystem) = v/solidangle(U,S)
A² [ϕ²] 統一

二次元角度または `solidangle` (rad²) の範囲、単位換算係数。

```

Julia julia> solidangle(CGS,Metric) # rad²⋅rad⁻² 𝟏 = 1.0 [𝟙]/[𝟙] ガウス -> メトリック ```
