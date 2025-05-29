```
struct DerSPMF{T<:AbstractMatrix,FDtype,TT<:Number} <: AbstractSPMF{T}
```

DerSPMFは、行列と関数の積の和によって定義されたNEPの表現です[`SPMF_NEP`](@ref)。この形式は、指定された`σ`に対する[`compute_Mlincomb`](@ref)の実行をより効率的にします。
