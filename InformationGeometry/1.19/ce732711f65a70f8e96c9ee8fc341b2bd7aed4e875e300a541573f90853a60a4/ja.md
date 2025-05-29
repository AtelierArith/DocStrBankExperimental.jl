```
ProfileBox(DM::AbstractDataModel, Fs::AbstractVector{<:AbstractInterpolation}, Confnum::Real=1.) -> HyperCube
```

信頼度 `Confnum` に関連する信頼領域を補間された尤度プロファイルから境界付ける `HyperCube` を構築します。
