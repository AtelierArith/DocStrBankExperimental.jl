```
function apply_voltage_bounds!(
    pmitd_data::Dict{String,<:Any};
    vm_lb::Union{Real,Missing}=0.9,
    vm_ub::Union{Real,Missing}=1.1
)
```

バスの電圧に基づいて、対応する電圧制限の変換をすべてのバスに適用し、`pmd` 辞書にスケーリングされた上限 (`vm_ub`) と下限 (`vm_lb`) を適用します。
