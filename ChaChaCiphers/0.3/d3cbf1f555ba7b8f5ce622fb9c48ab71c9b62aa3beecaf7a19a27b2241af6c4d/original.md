```
CUDAChaChaStream <: AbstractChaChaStream
```

`CUDAChaChaStream` is a CUDA-compatible ChaCha keystream generator for GPU CRNG.

## Examples

Create a `CUDAChaChaStream` with a randomized key, and sample some random numbers with it:

```julia
julia> rng = CUDAChaChaStream();

julia> x = CuVector{Float32}(undef, 2^10);
```

See also: [`ChaChaStream`](@ref)
