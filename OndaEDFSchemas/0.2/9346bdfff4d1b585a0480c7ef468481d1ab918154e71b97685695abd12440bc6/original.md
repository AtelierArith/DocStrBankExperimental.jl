```
@version FilePlanV2 > PlanV2 begin
    edf_signal_index::Int
    onda_signal_index::Int
end
```

A Legolas-generated record type representing one EDF signal-to-Onda channel conversion, which includes the columns of a [`PlanV2`](@ref) and additional file-level context:

  * `edf_signal_index` gives the index of the `signals` in the source `EDF.File` corresponding to this row
  * `onda_signal_index` gives the index of the output `Onda.Samples`.

Note that while the EDF index does correspond to the actual index in `edf.signals`, some Onda indices may be skipped in the output, so `onda_signal_index` is only to indicate order and grouping.
