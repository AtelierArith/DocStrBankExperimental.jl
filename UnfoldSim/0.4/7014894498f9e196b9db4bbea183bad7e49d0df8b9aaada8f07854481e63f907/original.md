```
magnitude(lf::AbstractArray{T,3}, orientation::AbstractArray{T,2}) where {T<:Real}
```

Return the magnitude of the leadfield `lf` along the given `orientation`.

# Arguments

  * `lf::AbstractArray{T,3}`: Leadfield with the dimensions `electrodes x sources x spatial dimension`.
  * `orientation::AbstractArray{T,2}`: Source orientations with the dimensions `sources x spatial dimensions`.

# Examples

```julia-repl
# Specify the leadfield (often given by a headmodel)
julia> lf = cat([1 0; 0 1; 0 0], [1 1; 0 0; 0.5 0.5], dims=3);

# Specify the source orientations
julia> ori = [1.0 0; 0 1]

# Calculate the magnitude
julia> magnitude(lf, ori)
3×2 Matrix{Float64}:
 1.0  1.0
 0.0  0.0
 0.0  0.5
```
