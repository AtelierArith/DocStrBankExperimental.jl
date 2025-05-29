```
get_ensemble_fit(ensemble_scaling::EnsembleScaling; precision::Real = 1e-1)
```

エンセmblescalingデータ`ensemble_scaling`の[`EnsembleFit`](@ref)オブジェクトとしてエンセmblescalingフィットデータを返し、データが相対精度`precision`にフィットしていない場合は警告を表示します。
