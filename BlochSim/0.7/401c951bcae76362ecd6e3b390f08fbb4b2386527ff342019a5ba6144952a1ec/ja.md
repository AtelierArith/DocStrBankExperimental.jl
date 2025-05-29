```
Magnetization(x, y, z)
Magnetization{T}()
Magnetization()
```

3D 磁化ベクトルを表す可変の `Magnetization` オブジェクトを作成します。

# プロパティ

  * `x::Real`: 磁化ベクトルの x 成分
  * `y::Real`: 磁化ベクトルの y 成分
  * `z::Real`: 磁化ベクトルの z 成分

# 例

```jldoctest
julia> M = Magnetization()
Magnetization vector with eltype Float64:
 Mx = 0.0
 My = 0.0
 Mz = 0.0

julia> M.x = 1; M.y = 2; M.z = 3; M
Magnetization vector with eltype Float64:
 Mx = 1.0
 My = 2.0
 Mz = 3.0
```
