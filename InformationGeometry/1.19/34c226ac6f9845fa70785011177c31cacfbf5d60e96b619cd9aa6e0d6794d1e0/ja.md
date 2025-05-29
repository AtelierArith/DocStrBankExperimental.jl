```
PredictionProfiles(DM::AbstractDataModel, yComp::Int, Ts::AbstractVector; Confnum::Real=2, dof::Int=DOF(DM), OffsetToZero::Bool=false, kwargs...)
```

コンポーネント `yComp` の予測に対する予測プロファイルのセットを、独立変数 `Ts` のさまざまな値で計算します。予測プロファイルは、中間的に生成された検証プロファイル [`ValidationProfiles`](@ref) を用いて計算されます。ほとんどの他の kwargs は `ParameterProfiles` 関数に渡され、したがって最適化器にも渡されます。例えば、[`ParameterProfiles`](@ref) や [`InformationGeometry.minimize`](@ref) を参照してください。
