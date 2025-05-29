```
precision(<:Union{Arf, Arb, Acb, arf_struct, arb_struct, acb_struct})
precision(<:Ptr{<:Union{arf_struct, arb_struct, acb_struct}})
precision(x::Union{arf_struct, arb_struct, acb_struct})
precision(x::Ptr{<:Union{arf_struct, arb_struct, acb_struct}})
```

`Arblib` 演算に現在使用されているデフォルトの精度（ビット単位）を取得します。
