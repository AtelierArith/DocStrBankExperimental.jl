```
precision(<:Union{Arf, Arb, Acb, arf_struct, arb_struct, acb_struct})
precision(<:Ptr{<:Union{arf_struct, arb_struct, acb_struct}})
precision(x::Union{arf_struct, arb_struct, acb_struct})
precision(x::Ptr{<:Union{arf_struct, arb_struct, acb_struct}})
```

Get the default precision (in bits) currently used for `Arblib` arithmetic.
