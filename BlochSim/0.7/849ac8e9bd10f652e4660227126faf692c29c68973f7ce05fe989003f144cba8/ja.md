```
ExcitationMatrix(A)
ExcitationMatrix{T}()
ExcitationMatrix()
```

`ExcitationMatrix`オブジェクトを作成します。`MagnetizationMC`オブジェクトとの乗算は、マルチコンパートメント磁化の各成分を`ExcitationMatrix`で乗算する効果があります。

# プロパティ

  * `A::BlochMatrix{<:Real}`: 励起を記述するために使用される行列

# 例

```jldoctest
julia> E = ExcitationMatrix(BlochMatrix(0, 1, 0, 1, 0, 0, 0, 0, 1))
ExcitationMatrix{Int64}:
 0  1  0
 1  0  0
 0  0  1

julia> M = MagnetizationMC((1, 2, 3), (4, 5, 6))
2コンパートメント磁化ベクトル、eltype Int64:
 コンパートメント 1:
  Mx = 1
  My = 2
  Mz = 3
 コンパートメント 2:
  Mx = 4
  My = 5
  Mz = 6

julia> E * M
2コンパートメント磁化ベクトル、eltype Int64:
 コンパートメント 1:
  Mx = 2
  My = 1
  Mz = 3
 コンパートメント 2:
  Mx = 5
  My = 4
  Mz = 6
```
