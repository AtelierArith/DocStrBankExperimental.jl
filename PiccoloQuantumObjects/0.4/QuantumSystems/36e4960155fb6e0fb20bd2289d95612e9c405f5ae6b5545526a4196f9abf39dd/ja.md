```
QuantumSystem <: AbstractQuantumSystem
```

量子力学の動力学と適切な勾配を格納するための構造体。

# フィールド

  * `H::Function`: 減衰を除くハミルトニアン関数: a -> H(a)。
  * `G::Function`: 減衰を含む同型生成子関数: a -> G(a)。
  * `∂G::Function`: 生成子ヤコビアン関数: a -> ∂G(a)。
  * `levels::Int`: システム内のレベル数。
  * `n_drives::Int`: システム内のドライブ数。

# コンストラクタ

  * QuantumSystem(H*drift::AbstractMatrix{<:Number}, H*drives::Vector{<:AbstractMatrix{<:Number}}; kwargs...)
  * QuantumSystem(H_drift::AbstractMatrix{<:Number}; kwargs...)
  * QuantumSystem(H_drives::Vector{<:AbstractMatrix{<:Number}}; kwargs...)
  * QuantumSystem(H::Function, n_drives::Int; kwargs...)
