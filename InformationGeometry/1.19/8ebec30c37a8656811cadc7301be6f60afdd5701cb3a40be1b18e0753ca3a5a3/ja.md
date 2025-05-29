```
ProfileBox(PV::ParameterProfilesView, Confnum::Real=1; Interp=DataInterpolations.QuadraticInterpolation, kwargs...)
```

信頼度 `Confnum` に関連する信頼領域を補間された尤度プロファイルから境界付ける `HyperCube` を構築します。
