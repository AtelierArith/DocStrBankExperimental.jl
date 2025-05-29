```
rbiquat(T::Type)
```

型 `T` の値を縮小されたバイクォータニオンとして表すことができる適切な型を返します。`typeof(rbiquat(zero(T)))` と同等です。

# 例

```jldoctest
julia> rbiquat(RBiQuaternion{Int})
RBiQuaternion{Int64}

julia> rbiquat(Int)
RBiQuaternion{Int64}
```
