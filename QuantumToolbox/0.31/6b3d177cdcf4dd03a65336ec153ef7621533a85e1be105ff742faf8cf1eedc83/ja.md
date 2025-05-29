```
correlation_2op_1t(H::AbstractQuantumObject,
    ψ0::Union{Nothing,QuantumObject},
    τlist::AbstractVector,
    c_ops::Union{Nothing,AbstractVector,Tuple},
    A::QuantumObject,
    B::QuantumObject;
    reverse::Bool=false,
    kwargs...)
```

二時相関関数（時間座標が一つだけの）を返します。二つの演算子 $\hat{A}$ と $\hat{B}$ に対して、$\left\langle \hat{A}(\tau) \hat{B}(0) \right\rangle$ を与えられた初期状態 $|\psi_0\rangle$ に対して計算します。

初期状態 `ψ0` が `nothing` として与えられた場合、[`steadystate`](@ref) が初期状態として使用されます。これは `H` が定数である場合にのみ実装されています（[`QuantumObject`](@ref)）。

`reverse=true` の場合、相関関数は $\left\langle \hat{A}(0) \hat{B}(\tau) \right\rangle$ として計算されます。
