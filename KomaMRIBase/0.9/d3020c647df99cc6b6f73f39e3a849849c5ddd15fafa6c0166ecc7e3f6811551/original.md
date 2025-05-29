```
obj = Phantom(name, x, y, z, ρ, T1, T2, T2s, Δw, Dλ1, Dλ2, Dθ, motion)
```

The Phantom struct. Most of its field names are vectors, with each element associated with a property value representing a spin. This struct serves as an input for the simulation.

# Arguments

  * `name`: (`::String`) phantom name
  * `x`: (`::AbstractVector{T<:Real}`, `[m]`) spin x-position vector
  * `y`: (`::AbstractVector{T<:Real}`, `[m]`) spin y-position vector
  * `z`: (`::AbstractVector{T<:Real}`, `[m]`) spin z-position vector
  * `ρ`: (`::AbstractVector{T<:Real}`) spin proton density vector
  * `T1`: (`::AbstractVector{T<:Real}`, `[s]`) spin T1 parameter vector
  * `T2`: (`::AbstractVector{T<:Real}`, `[s]`) spin T2 parameter vector
  * `T2s`: (`::AbstractVector{T<:Real}`, `[s]`) spin T2s parameter vector
  * `Δw`: (`::AbstractVector{T<:Real}`, `[rad/s]`) spin off-resonance parameter vector
  * `Dλ1`: (`::AbstractVector{T<:Real}`) spin Dλ1 (diffusion) parameter vector
  * `Dλ2`: (`::AbstractVector{T<:Real}`) spin Dλ2 (diffusion) parameter vector
  * `Dθ`: (`::AbstractVector{T<:Real}`) spin Dθ (diffusion) parameter vector
  * `motion`: (`::Union{NoMotion, Motion{T<:Real} MotionList{T<:Real}}`) motion

# Returns

  * `obj`: (`::Phantom`) Phantom struct

# Examples

```julia-repl
julia> obj = Phantom(x=[0.0])

julia> obj.ρ
```
