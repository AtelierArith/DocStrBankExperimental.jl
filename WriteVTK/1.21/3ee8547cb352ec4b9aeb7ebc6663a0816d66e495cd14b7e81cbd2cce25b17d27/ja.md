```
vtk_grid(filename::AbstractString,
         x::AbstractVector{T}, y::AbstractVector{T}, [z::AbstractVector{T}];
         kwargs...)
```

2Dまたは3D直交グリッド（`.vtr`）ファイルを作成します。

座標は別々のベクトル `x`、`y`、`z` で指定されます。

# 例

```jldoctest
julia> vtk = vtk_grid("abc", [0., 0.2, 0.5], collect(-2.:0.2:3), [1., 2.1, 2.3])
VTKファイル 'abc.vtr' (RectilinearGridファイル、オープン)
```
