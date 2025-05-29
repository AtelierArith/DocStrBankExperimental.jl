```
vtk_grid(filename, x::AbstractRange{T}, y::AbstractRange{T}, [z::AbstractRange{T}];
         kwargs...)
```

画像データ（`.vti`）ファイルを作成します。

各方向に沿って、グリッドはAbstractRangeオブジェクトで指定されます。

# 例

```jldoctest
julia> vtk = vtk_grid("abc", 1:0.2:5, 2:1.:3, 4:1.:5)  # 3Dデータセット
VTKファイル 'abc.vti' (ImageDataファイル, 開く)

julia> vtk = vtk_grid("abc", 1:5, 2:1.:3, range(4, 5; length = 3))  # 異なる種類の範囲
VTKファイル 'abc.vti' (ImageDataファイル, 開く)

julia> vtk = vtk_grid("abc", 1:0.2:5, 2:1.:3)  # 2Dデータセット
VTKファイル 'abc.vti' (ImageDataファイル, 開く)

julia> vtk = vtk_grid("def",
                      LinRange(0., 5., 10),
                      LinRange(0., 2π, 16),
                      LinRange(1., 10., 12))
VTKファイル 'def.vti' (ImageDataファイル, 開く)

```
