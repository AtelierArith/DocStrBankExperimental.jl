```
measure_double_occ(Gup::AbstractMatrix{T}, Gdn::AbstractMatrix{T}, a::Int, unit_cell::UnitCell) where {T}
```

Measure the double-occupancy $\langle \hat{n}_{\uparrow,a} \hat{n}_{\downarrow,a} \rangle$ for orbital species $a,$ given both the spin-up and spin-down equal-time Green's function matrices $G_\uparrow(\tau,\tau)$ and $G_\downarrow(\tau,\tau)$ respectively.
