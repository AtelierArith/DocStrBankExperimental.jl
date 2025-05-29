```
OpenQuantumSystem <: AbstractQuantumSystem
```

オープン量子ダイナミクスと適切な勾配を格納するための構造体です。

# 追加フィールド

  * `dissipation_operators::Vector{AbstractMatrix}`: 減衰演算子。

[`QuantumSystem`](@ref)も参照してください。

# コンストラクタ

  * OpenQuantumSystem(       H*drift::AbstractMatrix{<:Number},       H*drives::AbstractVector{<:AbstractMatrix{<:Number}}       dissipation_operators::AbstractVector{<:AbstractMatrix{<:Number}};       kwargs...   )
  * OpenQuantumSystem(       H*drift::Matrix{<:Number}, H*drives::AbstractVector{Matrix{<:Number}};       dissipation_operators::AbstractVector{<:AbstractMatrix{<:Number}}=Matrix{ComplexF64}[],       kwargs...   )
  * OpenQuantumSystem(H_drift::Matrix{<:Number}; kwargs...)
  * OpenQuantumSystem(H_drives::Vector{Matrix{<:Number}}; kwargs...)
  * OpenQuantumSystem(H::Function, n_drives::Int; kwargs...)
