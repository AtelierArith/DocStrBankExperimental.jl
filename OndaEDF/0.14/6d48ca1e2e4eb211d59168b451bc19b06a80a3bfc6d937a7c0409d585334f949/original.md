```
struct ConvertedSamples
    samples::Union{Samples,Missing}
    channel_plans::Vector{FilePlanV4}
    sensor_label::Union{String,Missing}
end
```

Represents a group of `EDF.Signal`s which have been converted into a single `Onda.Samples` (e.g. by [`edf_to_onda_samples`](@ref)).  The `channel_plans` are the [`FilePlanV4`s](@ref FilePlanV4) that were used to do the conversion.  The `sensor_label` field is the single unique value of the `sensor_label` fields of the `channel_plans`.

If conversion failed for any reason, `samples` will be `missing`.  Any runtime errors encountered during conversion will be stored in the `error` field of the `channel_plans`.

## Convenience functions for storing converted samples

The converted samples are *in-memory* `Onda.Samples` objects that usually need to be persisted to some external storage.  OndaEDF.jl implements methods for [`Onda.store`](@ref) with a `ConvertedSamples` argument which will extract the wrapped `samples` and `Onda.store` them.  When the wrapped `samples` are `missing`, these methods return `missing.` When the `Onda.SignalV2`-returning method with arguments for `recording` and `start` is called, the `sensor_label` is propagated by default (but may be overridden).

## Convenience functions for `EDF.File`-level collections

Conversion of an entire `EDF.File` via [`edf_to_onda_samples`](@ref) returns a `Vector{ConvertedSamples}`.

The [`get_plan`](@ref) function will collate the plans for a `Vector{ConvertedSamples}` into a single table that is suitable for passing to `Legolas.write`.

The [`get_samples`](@ref) function extracts the converted samples from a `Vector{ConvertedSamples}`.  By default, this function will skip any samples that are `missing`, unless called with a keyword argument `skipmissing=false`.
