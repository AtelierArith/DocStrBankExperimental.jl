```
rbiquat(T::Type)
```

Return an appropriate type that can represent a value of type `T` as a reduced biquaternion. Equivalent to `typeof(rbiquat(zero(T)))`.

# Examples

```jldoctest
julia> rbiquat(RBiQuaternion{Int})
RBiQuaternion{Int64}

julia> rbiquat(Int)
RBiQuaternion{Int64}
```
