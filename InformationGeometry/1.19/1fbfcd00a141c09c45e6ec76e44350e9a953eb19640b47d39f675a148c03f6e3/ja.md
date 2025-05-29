```
MincedBoundaries(DM::AbstractDataModel, Planes::AbstractVector{<:Plane}, Confnum::Real=1.; tol::Real=1e-9, ADmode::Val=Val(:ForwardDiff), meth=Tsit5(), mfd::Bool=false)
```

レベル `Confnum` の信頼境界を `Planes` と交差させ、この交差をパラメータ化する `ODESolution` を計算します。
