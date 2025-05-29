```
ConfidenceRegion(DM::AbstractDataModel, Confnum::Real=1.; tol::Real=1e-9, meth=Tsit5(), mfd::Bool=false, ADmode::Val=Val(:ForwardDiff), parallel::Bool=false, Dirs::Tuple{Int,Int,Int}=(1,2,3), N::Int=30)
```

レベル `Confnum` の信頼領域を計算します。`pdim(DM) > 2` の場合、信頼領域はキーワード `Dirs` で指定された方向の `Plane` のファミリーによって交差されます。この場合、`Plane` とその埋め込まれた2D信頼境界がそれぞれ最初と二番目の引数として返されます。
