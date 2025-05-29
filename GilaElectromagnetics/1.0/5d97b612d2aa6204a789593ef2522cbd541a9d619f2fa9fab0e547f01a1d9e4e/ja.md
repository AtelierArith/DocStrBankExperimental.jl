```
function GlaOprMem(cmpInf::GlaKerOpt, trgVol::GlaVol,
srcVol::Union{GlaVol,Nothing}=nothing, 
egoFur::Union{AbstractArray{<:AbstractArray{T}},
Nothing}=nothing)::GlaOprMem where T<:Union{ComplexF64,ComplexF32}
```

グリーン関数演算子のメモリを準備します。単一のGlaVolまたは同一のソースとターゲットボリュームで呼び出されると、自己構築を生成します。
