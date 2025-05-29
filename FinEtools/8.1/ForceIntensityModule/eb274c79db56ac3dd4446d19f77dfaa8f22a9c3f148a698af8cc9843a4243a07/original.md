```
updateforce!(self::ForceIntensity, XYZ::Matrix{T}, tangents::Matrix{T}, feid::IT, qpid::IT) where {T<:Number, IT<:Integer}
```

Update the force intensity vector.

Returns a vector (stored in the cache `self.cache`).
