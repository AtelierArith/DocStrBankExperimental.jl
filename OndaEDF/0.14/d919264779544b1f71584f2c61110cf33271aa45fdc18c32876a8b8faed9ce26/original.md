```
store_edf_as_onda(edf::EDF.File, onda_dir, recording_uuid::UUID=uuid4();
                  custom_extractors=STANDARD_EXTRACTORS, import_annotations::Bool=true,
                  signals_prefix="edf", annotations_prefix=signals_prefix)
```

Convert an EDF.File to `Onda.Samples` and `Onda.Annotation`s, store the samples in `$path/samples/`, and write the Onda signals and annotations tables to `$path/$(signals_prefix).onda.signals.arrow` and `$path/$(annotations_prefix).onda.annotations.arrow`.  The default prefix is "edf", and if a prefix is provided for signals but not annotations both will use the signals prefix.  The prefixes cannot reference (sub)directories.

Returns `(; recording_uuid, signals, annotations, signals_path, annotations_path, plan)`.

This is a convenience function that first formulates an import plan via [`plan_edf_to_onda_samples`](@ref), and then immediately executes this plan with [`edf_to_onda_samples`](@ref).

The samples and executed plan are returned; it is **strongly advised** that you review the plan for un-extracted signals (where `:sensor_type` or `:channel` is `missing`) and errors (non-`nothing` values in `:error`).

Groups of `EDF.Signal`s are mapped as channels to `Onda.Samples` via [`plan_edf_to_onda_samples`](@ref).  The caller of this function can control the plan via the `labels` and `units` keyword arguments, all of which are forwarded to [`plan_edf_to_onda_samples`](@ref).

`EDF.Signal` labels that are converted into Onda channel names undergo the following transformations:

  * the label is whitespace-stripped, parens-stripped, and lowercased
  * trailing generic EDF references (e.g. "ref", "ref2", etc.) are dropped
  * any instance of `+` is replaced with `_plus_` and `/` with `_over_`
  * all component names are converted to their "canonical names" when possible (e.g. "3" in an ECG-matched channel name will be converted to "iii").

If more control (e.g. preprocessing signal labels) is required, callers should use [`plan_edf_to_onda_samples`](@ref) and [`edf_to_onda_samples`](@ref) directly, and `Onda.store` the resulting samples manually.

See the OndaEDF README for additional details regarding EDF formatting expectations.
