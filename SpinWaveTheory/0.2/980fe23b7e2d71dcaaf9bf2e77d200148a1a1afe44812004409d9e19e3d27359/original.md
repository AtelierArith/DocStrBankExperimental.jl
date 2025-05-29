```
rotation(destination::AbstractVector{<:Number}; kwargs...) -> SMatrix{3, 3}
rotation(destination::Tuple{Number, Number}; unit::Symbol=:radian) -> SMatrix{3, 3}
```

Get the rotation matrix which rotates `[0, 0, 1]` to the direction of the `destination` vector.
