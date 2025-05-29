```
projector(x::MPS; <keyword argument>) -> MPO
```

Computes the projector onto the state `x`. In Dirac notation, this is the operation `|x⟩⟨x|/|⟨x|x⟩|²`.

Use keyword arguments to control the level of truncation, which are the same as those accepted by `contract(::MPO, ::MPO; kw...)`.

# Keywords

  * `normalize::Bool=true`: whether or not to normalize the input MPS before  forming the projector. If `normalize==false` and the input MPS is not  already normalized, this function will not output a proper project, and  simply outputs `outer(x, x) = |x⟩⟨x|`, i.e. the projector scaled by `norm(x)^2`.
  * truncation keyword arguments accepted by `contract(::MPO, ::MPO; kw...)`.

See also [`outer`](@ref), [`contract`](@ref).
