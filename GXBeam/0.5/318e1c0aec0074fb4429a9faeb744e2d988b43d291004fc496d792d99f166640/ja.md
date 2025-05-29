```
extract_element_states(system, assembly, x = system.x, dx = system.dx;
    prescribed_conditions = Dict{Int,PrescribedConditions{Float64}}())
```

解決ベクトル `x` に対応する各要素の状態変数を返します（[`ElementState`](@ref）を参照）。
