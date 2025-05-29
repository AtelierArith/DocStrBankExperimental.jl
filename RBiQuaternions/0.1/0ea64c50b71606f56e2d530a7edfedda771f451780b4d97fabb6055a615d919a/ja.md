```
rbiquat(w, [x, y, z])
```

実数または配列を縮小バイクォータニオンに変換します。`x, y, z`はデフォルトでゼロです。

# 例

```jldoctest
julia> rbiquat(7)
RBiQuaternion{Int64}(7, 0, 0, 0)

julia> rbiquat(1.0, 2, 3, 4)
RBiQuaternionF64(1.0, 2.0, 3.0, 4.0)

julia> rbiquat([1, 2, 3])
3-element Vector{Quaternion{Int64}}:
 RBiQuaternion{Int64}(1, 0, 0, 0)
 RBiQuaternion{Int64}(2, 0, 0, 0)
 RBiQuaternion{Int64}(3, 0, 0, 0)
```
