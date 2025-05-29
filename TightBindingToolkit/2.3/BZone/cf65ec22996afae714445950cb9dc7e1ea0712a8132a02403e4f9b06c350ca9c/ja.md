```julia
FillBZ!(bz::BZ, uc::UnitCell ; shift::Vector{Float64}=zeros(Float64, length(uc.primitives)))
```

`BZ`オブジェクトを、`BZ(gridSize)`で初期化された後に、関連する属性で埋めます。
