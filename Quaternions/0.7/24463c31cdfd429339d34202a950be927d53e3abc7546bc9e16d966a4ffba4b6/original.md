```
quat(T::Type)
```

Return an appropriate type that can represent a value of type `T` as a quaternion. Equivalent to `typeof(quat(zero(T)))`.

# Examples

```jldoctest
julia> quat(Quaternion{Int})
Quaternion{Int64}

julia> quat(Int)
Quaternion{Int64}
```
