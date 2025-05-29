```julia
mutable struct KeplerianState{F, LU, TU, AU} <: GeneralAstrodynamics.States.StateVector{F, LU, TU, AU, (e = 1, a = 2, i = 3, Ω = 4, ω = 5, ν = 6)}
```

長さ6のケプラー状態ベクトル。内部ではデータを格納するために `MVector` と `LVector` を使用します。データは `e, a, i, Ω, ω, ν` というラベルを介してアクセスできます。
