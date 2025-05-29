```
updatenormal!(
    self::SurfaceNormal,
    XYZ::AbstractVecOrMat{<:Real},
    tangents::AbstractMatrix{<:Real},
    feid::IT,
    qpid::IT,
) where {IT}
```

サーフェス法線ベクトルを更新します。

キャッシュに保存された法線ベクトルを返します。
