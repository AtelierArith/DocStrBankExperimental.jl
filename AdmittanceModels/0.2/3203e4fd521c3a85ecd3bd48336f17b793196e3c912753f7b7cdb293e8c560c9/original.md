```
short_ports_except(am::AdmittanceModel{T}, ports::AbstractVector{T}) where T
short_ports_except(am::AdmittanceModel{T}, ports::Vararg{T}) where T
```

Replace all ports with short circuits, except those specified.
