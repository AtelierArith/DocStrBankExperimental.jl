```
ValidationProfiles(DM::AbstractDataModel, yComp::Int, Ts::AbstractVector; Confnum::Real=2, dof::Int=DOF(DM), OffsetToZero::Bool=false, kwargs...)
```

コンポーネント `yComp` の予測に対する検証プロファイルのセットを、独立変数 `Ts` のさまざまな値で計算します。架空の検証データポイントの不確実性は、キーワード引数 `σv` を介してオプションで選択できます。他のほとんどの kwargs は `ParameterProfiles` 関数に渡され、したがって最適化器にも渡されます。例えば、[`ParameterProfiles`](@ref) や [`InformationGeometry.minimize`](@ref) を参照してください。
