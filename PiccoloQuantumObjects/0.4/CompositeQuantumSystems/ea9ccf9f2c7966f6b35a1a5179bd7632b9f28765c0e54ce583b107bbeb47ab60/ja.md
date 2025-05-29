```
lift(operator::AbstractMatrix{<:Number}, i::Int, subsystem_levels::Vector{Int})
lift(operator::AbstractMatrix{<:Number}, i::Int, n_qubits::Int; kwargs...)
lift(operators::AbstractVector{<:AbstractMatrix{T}}, indices::AbstractVector{Int}, subsystem_levels::Vector{Int})
lift(operators::AbstractVector{<:AbstractMatrix{T}}, indices::AbstractVector{Int}, n_qubits::Int; kwargs...)
lift(operator::AbstractMatrix{T}, indices::AbstractVector{Int}, subsystem_levels::AbstractVector{Int})
lift(operator::AbstractMatrix{T}, indices::AbstractVector{Int}, n_qubits::Int; kwargs...)
```

`subsystem_levels`内の`i`-番目のサブシステムに作用する`operator`を、`subsystem_levels`全体にわたるオペレーターに持ち上げます。
