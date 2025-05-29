```
mat_fun_frechet(f, H::AbstractMatrix, h::Vector{AbstractMatrix}; kwargs...)
mat_fun_frechet(DD_F, Ψ::AbstractMatrix, h::Vector{AbstractMatrix})
```

Return the n-th order Fréchet derivative `d^nf(H)h[1]…h[n]`, assuming `f` is called as `f(x)`. See `mat_fun` for a description of possible keyword arguments.
