```
strictinterp(f_interp::Function, ts::AbstractTimeSeries, t::Real, indhint::Union{Nothing,Integer,<:RefValue{<:Integer}})
```

時刻 t::Real での単一補間を行い、より高速な検索のために indhint を提供します。t が時系列の範囲内にない場合は、TimeRecord{t, Missing} を返します。
