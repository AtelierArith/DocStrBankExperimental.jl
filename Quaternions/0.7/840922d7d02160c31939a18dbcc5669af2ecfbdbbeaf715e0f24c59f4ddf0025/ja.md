```
quat(w, [x, y, z])
```

実数または配列をクォータニオンに変換します。`x, y, z`はデフォルトでゼロです。

# 例

```jldoctest
julia> quat(7)
Quaternion{Int64}(7, 0, 0, 0)

julia> quat(1.0, 2, 3, 4)
QuaternionF64(1.0, 2.0, 3.0, 4.0)

julia> quat([1, 2, 3])
3-element Vector{Quaternion{Int64}}:
 Quaternion{Int64}(1, 0, 0, 0)
 Quaternion{Int64}(2, 0, 0, 0)
 Quaternion{Int64}(3, 0, 0, 0)
```
