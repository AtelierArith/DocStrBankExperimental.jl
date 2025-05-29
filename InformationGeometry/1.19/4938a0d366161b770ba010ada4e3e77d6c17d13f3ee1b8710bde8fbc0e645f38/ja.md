```
GenerateBoundary(DM::DataModel, u0::AbstractVector{<:Number}; tol::Real=1e-9, meth=Tsit5(), mfd::Bool=true) -> ODESolution
```

初期構成 `u0` に関連する信頼領域上に曲線を構築するための基本的な方法です。
