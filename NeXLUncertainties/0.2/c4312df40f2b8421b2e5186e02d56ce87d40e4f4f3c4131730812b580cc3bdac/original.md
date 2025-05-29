```
uvs(labels::AbstractVector{<:Label}, values::AbstractVector{T}, covar::AbstractMatrix{T})  where { T <: Real }
uvs(labels::AbstractVector{<:Label}, values::AbstractVector{T}, vars::AbstractVector{T}) where { T <: Real }
uvs(values::Pair{<:Label,UncertainValue}...)
uvs(value::Pair{<:Label,UncertainValue})
uvs(values::Dict{<:Label,UncertainValue})
```

Various methods for constructing `UncertainValues` structures from varying types of inputs.
