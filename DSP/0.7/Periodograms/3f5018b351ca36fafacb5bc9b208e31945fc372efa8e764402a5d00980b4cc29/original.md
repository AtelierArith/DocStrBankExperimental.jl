```
mt_pgram!(output, s::AbstractVector{T}; onesided::Bool=eltype(s)<:Real,
    nfft::Int=nextfastfft(length(s)), fs::Real=1,
    nw::Real=4, ntapers::Int=ceil(Int, 2nw)-1,
    window::Union{AbstractMatrix,Nothing}=nothing) where T<:Number
mt_pgram!(output::AbstractVector, signal::AbstractVector, config::MTConfig) -> Periodogram
```

Computes a multitapered periodogram, storing the output in `output`. Arguments:

  * `signal::AbstractVector`: should be of length `config.n_samples`
  * `output::AbstractVector`: should be of length `length(config.freq)`

Optionally pass an [`MTConfig`](@ref) object to preallocate temporary variables and choose configuration settings; otherwise, keyword arguments may be passed to choose those settings.

Returns a `Periodogram`.

See also [`mt_pgram`](@ref) and [`MTConfig`](@ref).
