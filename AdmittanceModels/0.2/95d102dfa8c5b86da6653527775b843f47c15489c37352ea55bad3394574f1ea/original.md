An abstract representation of a linear mapping from inputs `x` to outputs `y` of the form `YΦ = Px`, `y = QᵀΦ`. Subtypes U <: AdmittanceModel are expected to implement:

```
get_Y(am::U)
get_P(am::U)
get_Q(am::U)
get_ports(am::U)
partial_copy(am::U; Y, P, ports)
compatible(AbstractVector{U})
```
