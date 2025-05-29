```
onda_to_edf(samples::AbstractVector{<:Samples}, annotations=[]; kwargs...)
```

Return an `EDF.File` containing signal data converted from a collection of Onda [`Samples`](https://beacon-biosignals.github.io/Onda.jl/stable/#Samples-1) and (optionally) annotations from an [`annotations` table](https://beacon-biosignals.github.io/Onda.jl/stable/#*.onda.annotations.arrow-1).

Following the Onda v0.5 format, `annotations` can be any Tables.jl-compatible table (DataFrame, Arrow.Table, NamedTuple of vectors, vector of NamedTuples) which follows the [annotation schema](https://beacon-biosignals.github.io/Onda.jl/stable/#*.onda.annotations.arrow-1).

Each `EDF.Signal` in the returned `EDF.File` corresponds to a channel of an input `Onda.Samples`.

The ordering of `EDF.Signal`s in the output will match the order of the input collection of `Samples` (and within each channel grouping, the order of the samples' channels).

!!! note
    EDF signals are encoded as Int16, while Onda allows a range of different sample types, some of which provide considerably more resolution than Int16. During export, re-encoding may be necessary if the encoded Onda samples cannot be represented directly as Int16 values.  In this case, new encoding (resolution and offset) will be chosen based on the minimum and maximum values actually present in each *signal* in the input Onda Samples.  Thus, it may not always be possible to losslessly round trip Onda-formatted datasets to EDF and back.

