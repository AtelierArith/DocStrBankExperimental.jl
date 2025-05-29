```
correlation_3op_2t(H::AbstractQuantumObject,
    ψ0::Union{Nothing,QuantumObject},
    tlist::AbstractVector,
    τlist::AbstractVector,
    c_ops::Union{Nothing,AbstractVector,Tuple},
    A::QuantumObject,
    B::QuantumObject,
    C::QuantumObject;
    kwargs...)
```

三つの演算子 $\hat{A}$, $\hat{B}$, $\hat{C}$ の二時相関関数 $\left\langle \hat{A}(t) \hat{B}(t + \tau) \hat{C}(t) \right\rangle$ を、与えられた初期状態 $|\psi_0\rangle$ に対して返します。

初期状態 `ψ0` が `nothing` として与えられた場合、[`steadystate`](@ref) が初期状態として使用されます。これは `H` が定数である場合にのみ実装されています（[`QuantumObject`](@ref)）。
