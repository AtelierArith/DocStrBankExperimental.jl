```
short_ports(am::AdmittanceModel{T}, ports::AbstractVector{T}) where T
short_ports(am::AdmittanceModel{T}, ports::Vararg{T}) where T
```

与えられたポートを短絡回路に置き換えます。
