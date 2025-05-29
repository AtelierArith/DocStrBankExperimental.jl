```
BodemagWorkspace(sys::LTISystem, N::Int)
BodemagWorkspace(sys::LTISystem, ω::AbstractVector)
BodemagWorkspace(R::Array{Complex{T}, 3}, mag::Array{T, 3})
BodemagWorkspace{T}(ny, nu, N)
```

Generate a workspace object for use with the in-place function [`bodemag!`](@ref). `N` is the number of frequency points, alternatively, the input `ω` can be provided instead of `N`. Note: for threaded applications, create one workspace object per thread. 

# Arguments:

  * `mag`: The output array ∈ 𝐑(ny, nu, nω)
  * `R`: Frequency-response array ∈ 𝐂(ny, nu, nω)
