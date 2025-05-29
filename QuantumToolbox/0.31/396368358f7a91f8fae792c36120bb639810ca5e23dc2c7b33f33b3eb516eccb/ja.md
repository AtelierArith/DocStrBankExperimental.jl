```
correlation_2op_2t(H::AbstractQuantumObject,
    ψ0::Union{Nothing,QuantumObject},
    tlist::AbstractVector,
    τlist::AbstractVector,
    c_ops::Union{Nothing,AbstractVector,Tuple},
    A::QuantumObject,
    B::QuantumObject;
    reverse::Bool=false,
    kwargs...)
```

二時相関関数 $\hat{A}$ と $\hat{B}$ のための関数を返します： $\left\langle \hat{A}(t + \tau) \hat{B}(t) \right\rangle$ で、与えられた初期状態 $|\psi_0\rangle$ に対して。

初期状態 `ψ0` が `nothing` として与えられた場合、[`steadystate`](@ref) が初期状態として使用されます。これは、`H` が定数である場合にのみ実装されています（[`QuantumObject`](@ref)）。

`reverse=true` の場合、相関関数は $\left\langle \hat{A}(t) \hat{B}(t + \tau) \right\rangle$ として計算されます。
