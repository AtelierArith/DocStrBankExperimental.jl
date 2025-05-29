```
lift(operator::AbstractMatrix{<:Number}, i::Int, subsystem_levels::Vector{Int})
lift(operator::AbstractMatrix{<:Number}, i::Int, n_qubits::Int; kwargs...)
lift(operators::AbstractVector{<:AbstractMatrix{T}}, indices::AbstractVector{Int}, subsystem_levels::Vector{Int})
lift(operators::AbstractVector{<:AbstractMatrix{T}}, indices::AbstractVector{Int}, n_qubits::Int; kwargs...)
lift(operator::AbstractMatrix{T}, indices::AbstractVector{Int}, subsystem_levels::AbstractVector{Int})
lift(operator::AbstractMatrix{T}, indices::AbstractVector{Int}, n_qubits::Int; kwargs...)
```

Lift an `operator` acting on the `i`-th subsystem within `subsystem_levels` to an operator acting on the entire system spanning `subsystem_levels`.
