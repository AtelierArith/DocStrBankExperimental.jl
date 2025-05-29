```
ProfileBox(P::ParameterProfiles, Confnum::Real=1; Interp=DataInterpolations.QuadraticInterpolation, kwargs...)
```

信頼度 `Confnum` に関連する信頼領域を補間された尤度プロファイルから囲む `HyperCube` を構築します。
