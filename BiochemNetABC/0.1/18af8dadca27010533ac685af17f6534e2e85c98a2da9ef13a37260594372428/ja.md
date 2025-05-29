`volatile_simulate(pm::ParametricModel, p_prior::AbstractVector{Float64})`

`simulate(pm::ParametricModel, p_prior::AbstractVector{Float64})`のボラティリティ版です。`pm`のモデルはSynchronizedModel型である必要があります（`typeof(pm.m) <: SynchronizedModel`）。これは、軌道ではなく`S::StateLHA`を返します。
