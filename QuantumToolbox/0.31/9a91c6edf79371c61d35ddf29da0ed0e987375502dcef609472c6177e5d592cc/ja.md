```
correlation_3op_1t(H::AbstractQuantumObject,
    ψ0::Union{Nothing,QuantumObject},
    τlist::AbstractVector,
    c_ops::Union{Nothing,AbstractVector,Tuple},
    A::QuantumObject,
    B::QuantumObject,
    C::QuantumObject;
    kwargs...)
```

三つの演算子 $\hat{A}$、$\hat{B}$、$\hat{C}$ の二時相関関数（時間座標は一つの $\tau$ のみ）を返します：$\left\langle \hat{A}(0) \hat{B}(\tau) \hat{C}(0) \right\rangle$、与えられた初期状態 $|\psi_0\rangle$ に対して。

初期状態 `ψ0` が `nothing` として与えられた場合、[`steadystate`](@ref) が初期状態として使用されます。これは `H` が定数である場合にのみ実装されています（[`QuantumObject`](@ref)）。
