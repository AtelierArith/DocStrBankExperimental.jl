```julia
struct FiniteExcited{A} <: MPSKit.Algorithm
```

有限MPSの励起のための変分最適化アルゴリズムで、エネルギーを最小化します。

$$
H - λᵢ |ψᵢ⟩⟨ψᵢ|
$$

## フィールド

  * `gsalg::Any`: 最適化アルゴリズム
  * `weight::Float64`: 前の状態との直交性を強制するためのエネルギーペナルティ
