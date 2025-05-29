Circuit{N}(moments::Vector{Moment}, mops::Union{Vector{<:MeasurementOperator},Nothing}=nothing) where {N}

Chain of quantum circuit gates in a circuit of `N` qubits. Constructed from vector of `AbstractCircuitGate` objects.
