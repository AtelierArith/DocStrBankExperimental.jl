```
Samples(data::AbstractMatrix, info::SamplesInfoV2, encoded::Bool;
        validate::Bool=Onda.VALIDATE_SAMPLES_DEFAULT[])
```

Return a `Samples` instance with the following fields:

  * `data::AbstractMatrix`: A matrix of sample data. The `i` th row of the matrix corresponds to the `i`th channel in `info.channels`, while the `j`th column corresponds to the `j`th multichannel sample.
  * `info::SamplesInfoV2`: The [`SamplesInfoV2`](@ref)-compliant value that describes the `Samples` instance.
  * `encoded::Bool`: If `true`, the values in `data` are LPCM-encoded as prescribed by the `Samples` instance's `info`. If `false`, the values in `data` have been decoded into the `info`'s canonical units.

If `validate` is `true`, [`Onda.validate_samples`](@ref) is called on the constructed `Samples` instance before it is returned.

Note that `getindex` and `view` are defined on `Samples` to accept normal integer indices, but also accept channel names or a regex to match channel names for row indices, and `TimeSpan` values for column indices; see `Onda/examples/tour.jl` for a comprehensive set of indexing examples.

Note also that "slices" copied from `s::Samples` via `getindex(s, ...)` may alias `s.info` in order to avoid excessive overhead. This means one should generally avoid directly mutating `s.info`, especially `s.info.channels`.

See also: [`load`](@ref), [`store`](@ref), [`encode`](@ref), [`encode!`](@ref), [`decode`](@ref), [`decode!`](@ref)
