```
refit!(m::RobustLinearModel, [y::FPVector];
                             wts::Union{Nothing, FPVector} = nothing,
                             offset::Union{Nothing, FPVector} = nothing,
                             quantile::Union{Nothing, AbstractFloat} = nothing,
                             ridgeλ::Union{Nothing, Real} = nothing,
                             kwargs...)
```

[`RobustLinearModel`](@ref)を再フィットします。

この関数は、`m`が正しく初期化されており、モデルが応答、重み、オフセット、分位数、およびリッジ収縮の新しい値で再フィットされることを前提としています。

新しい`quantile`を定義することは、[`GeneralizedQuantileEstimator`](@ref)に対してのみ可能です。

新しい`ridgeλ`を定義することは、[`RidgePred`](@ref)オブジェクトに対してのみ可能です。
