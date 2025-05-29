```
plan_edf_to_onda_samples(header, seconds_per_record; labels=STANDARD_LABELS,
                         units=STANDARD_UNITS)
plan_edf_to_onda_samples(signal::EDF.Signal, args...; kwargs...)
```

Formulate a plan for converting an EDF signal into Onda format.  This returns a Tables.jl row with all the columns from the signal header, plus additional columns for the `Onda.SamplesInfo` for this signal, and the `seconds_per_record` that is passed in here.

If no labels match, then the `channel` and `sensor_type` columns are `missing`; the behavior of other `SamplesInfo` columns is undefined; they are currently set to missing but that may change in future versions.

Any errors that are thrown in the process will be wrapped as `SampleInfoError`s and then printed with backtrace to a `String` in the `error` column.

## Matching EDF label to Onda labels

The `labels` keyword argument determines how Onda `channel` and signal `sensor_type` are extracted from the EDF label.

Labels are specified as an iterable of `signal_names => channel_names` pairs. `signal_names` should be an iterable of signal names, the first of which is the canonical name used as the Onda `sensor_type`.  Each element of `channel_names` gives the specification for one channel, which can either be a string, or a `canonical_name => alternates` pair.  Occurences of `alternates` will be replaces with `canonical_name` in the generated channel label.

Matching is determined *solely* by the channel names.  When matching, the signal names are only used to remove signal names occuring as prefixes (e.g., "[ECG] AVL") before matching channel names.  See [`match_edf_label`](@ref) for details, and see `OndaEDF.STANDARD_LABELS` for the default labels.

As an example, here is (a subset of) the default labels for ECG signals:

```julia
["ecg", "ekg"] => ["i" => ["1"], "ii" => ["2"], "iii" => ["3"],
                   "avl"=> ["ecgl", "ekgl", "ecg", "ekg", "l"],
                   "avr"=> ["ekgr", "ecgr", "r"], ...]
```

Matching is done in the order that `labels` iterates pairs, and will stop at the first match, with no warning if signals are ambiguous (although this may change in a future version)
