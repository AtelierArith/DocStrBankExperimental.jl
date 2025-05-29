```
mt_spectrogram(signal::AbstractVector, mt_config::MTConfig,
               n_overlap::Int=mt_config.n_samples >> 1) -> Spectrogram
```

Compute a multitaper spectrogram using an an [`MTConfig`](@ref) object to choose the window size. Note that all the workspace variables are contained in the [`MTConfig`](@ref) object, and this object can be re-used between spectrogram computations, so that only the output needs to be allocated.

Returns a `Spectrogram`.

See also [`mt_spectrogram!`](@ref).

## Example

```julia
signal1 = sin.(10_000) .+ randn(10_000)
mt_config = MTConfig{Float64}(1000) # 1000 samples per window
spec1 = mt_spectrogram(signal1, mt_config, 500)
signal2 = cos.(2_000) .+ randn(2_000)
spec2 = mt_spectrogram(signal2, mt_config, 250) # same `mt_config`, different signal, different overlap
```
