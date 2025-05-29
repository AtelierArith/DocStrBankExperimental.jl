```
quat(T::Type)
```

型 `T` の値をクォータニオンとして表現できる適切な型を返します。`typeof(quat(zero(T)))` と同等です。

# 例

```jldoctest
julia> quat(Quaternion{Int})
Quaternion{Int64}

julia> quat(Int)
Quaternion{Int64}
```
