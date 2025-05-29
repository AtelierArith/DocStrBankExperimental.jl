Circuit{N}(moments::Vector{Moment}, mops::Union{Vector{<:MeasurementOperator},Nothing}=nothing) where {N}

`N`量子ビットの回路における量子回路ゲートのチェーン。`AbstractCircuitGate`オブジェクトのベクターから構築されます。
