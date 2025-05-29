```
liouvillian_generalized(H::QuantumObject, fields::Vector, 
T_list::Vector; N_trunc::Int=size(H,1), tol::Float64=0.0, σ_filter::Union{Nothing, Real}=nothing)
```

ハーモニックオシレーターのバスに結合されたシステムの一般化されたリウヴィル方程式を構築します。

例えば、Settineri, Alessio, et al. "Dissipation and thermal noise in hybrid quantum systems in the ultrastrong-coupling regime." Physical Review A 98.5 (2018): 053834を参照してください。
