```julia
CreateUnitCell!(uc::UnitCell, param::Param , index::Int64=length(param.value))
CreateUnitCell!(uc::UnitCell, params::Vector{Param}, indices::Vector{Int64}=length.(getproperty.(params, :value)))
```

`param` に対応する結合を `UnitCell` に追加し、`param.value[index]` でスケーリングします。ブロードキャストされた呼び出しも含まれています。
