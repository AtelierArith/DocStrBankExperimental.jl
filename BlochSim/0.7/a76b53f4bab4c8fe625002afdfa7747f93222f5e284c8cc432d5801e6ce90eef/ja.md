```
MagnetizationMC((x1, y1, z1), ...)
MagnetizationMC{T}(N)
MagnetizationMC(N)
```

同じ物理的位置にある `N` 個の3D磁化ベクトルを表す `MagnetizationMC` オブジェクトを作成します。

`MagnetizationMC` オブジェクトをインデックス指定することで、i番目の成分磁化ベクトルにアクセスできます。さらに、`MagnetizationMC` オブジェクトを反復処理すると、各成分磁化ベクトルを順に処理します。

# プロパティ

  * `M::NTuple{N,Magnetization{<:Real}}`: 成分磁化ベクトルのリスト

# 例

```jldoctest
julia> M = MagnetizationMC((1, 2, 3), (4, 5, 6))
2コンパートメントの磁化ベクトル、eltype Int64:
 コンパートメント 1:
  Mx = 1
  My = 2
  Mz = 3
 コンパートメント 2:
  Mx = 4
  My = 5
  Mz = 6

julia> M[2]
磁化ベクトル、eltype Int64:
 Mx = 4
 My = 5
 Mz = 6

julia> foreach(m -> (m.x = 0; m.y = 1; m.z = 2), M)

julia> M
2コンパートメントの磁化ベクトル、eltype Int64:
 コンパートメント 1:
  Mx = 0
  My = 1
  Mz = 2
 コンパートメント 2:
  Mx = 0
  My = 1
  Mz = 2
```
