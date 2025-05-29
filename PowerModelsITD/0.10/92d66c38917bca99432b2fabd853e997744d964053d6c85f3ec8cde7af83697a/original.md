```
function apply_voltage_bounds!(
    pmitd_data::Dict{String,<:Any};
    vm_lb::Union{Real,Missing}=0.9,
    vm_ub::Union{Real,Missing}=1.1
)
```

Applies the corresponding transformation of voltage bounds to all buses based on per-unit upper (`vm_ub`) and lower (`vm_lb`) bounds, scaled by the bus' voltage, to the `pmd` dictionary.
