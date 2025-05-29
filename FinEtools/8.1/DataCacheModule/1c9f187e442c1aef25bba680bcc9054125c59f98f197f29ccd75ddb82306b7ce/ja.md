```
(c::DataCache)(
    XYZ::AbstractVecOrMat{<:Real},
    tangents::AbstractMatrix{<:Real},
    feid::IT,
    qpid::IT,
) where {IT<:Integer}
```

キャッシュを更新し、配列を取得します。
