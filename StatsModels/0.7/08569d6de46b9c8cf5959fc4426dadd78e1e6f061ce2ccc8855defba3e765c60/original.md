```
unprotect(term)
unprotect(::Protected{T})
```

Inside a [`@formula`], removes [`Protected`](@ref) status for the argument term(s).  This allows the [`@formula`](@ref)-specific interpretation of calls to `+`, `&`, `*`, and `~` to be restored inside an otherwise [`Protected`](@ref) context.

When called outside a `@formula`, unwraps `Protected{T}` to `T`.

# Example

```jldoctest; setup = :(using Random; Random.seed!(1))
julia> d = (y=rand(4), a=[1.:4;], b=rand(4));

julia> f = @formula(y ~ 1 - unprotect(a&b));

julia> modelmatrix(f, d)
4×1 Matrix{Float64}:
  0.08507099633716864
  0.6143837675082491
 -1.310541043656999
 -2.1220770547007453

julia> 1 .- d.a .* d.b
4-element Vector{Float64}:
  0.08507099633716864
  0.6143837675082491
 -1.310541043656999
 -2.1220770547007453
```
