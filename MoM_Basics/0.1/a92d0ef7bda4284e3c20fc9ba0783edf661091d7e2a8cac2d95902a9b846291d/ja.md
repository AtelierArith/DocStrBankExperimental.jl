```
sourceEfield(sources::Vector{ST}, rvec::AbstractVector{FT}) where {FT<:Real, ST<:ExcitingSource}
```

計算ソースベクトル `sources` がグローバル座標系で与えられた位置 `rvec` における遠方場電場。
