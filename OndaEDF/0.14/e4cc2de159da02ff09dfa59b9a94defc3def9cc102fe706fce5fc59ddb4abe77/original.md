```
edf_to_onda_samples(edf::EDF.File; kwargs...)
```

Read signals from an `EDF.File` into a [`Vector{ConvertedSamples}`](@ref ConvertedSamples). This is a convenience function that first formulates an import plan via [`plan_edf_to_onda_samples`](@ref), and then immediately executes this plan with [`edf_to_onda_samples`](@ref).

!!! warning
    This function is provided as a convenience for "quick and dirty" exploration.  In general, it is strongly adivsed to review the plan and make any necessary adjustments *before* execution.


A [`Vector{ConvertedSamples}`](@ref ConvertedSamples) is returned; use [`get_plan`](@ref) and [`get_samples`](@ref) to extract the executed plan and `Onda.Samples` respectively.  It is **strongly advised** that you review the output for un-extracted signals by investigating any `ConvertedSamples` where the `.samples` are `missing`.  Run-time errors during conversion are stored in the `:error` column of the `.channel_plans`, and any EDF Signals that could not be matched will have `missing` values in their `.channel_plans` for `:sensor_type`, `:channel`, or `:physical_unit`.

Collections of `EDF.Signal`s are mapped as channels to `Onda.Samples` via [`plan_edf_to_onda_samples`](@ref).  The caller of this function can control the plan via the `labels` and `units` keyword arguments, all of which are forwarded to [`plan_edf_to_onda_samples`](@ref).  If more control is required, first generate the plan, review and edit it as needed, and then execute by passing it as the second argument to `edf_to_onda_samples`.

`EDF.Signal` labels that are converted into Onda channel names undergo the following transformations:

  * the label is whitespace-stripped, parens-stripped, and lowercased
  * trailing generic EDF references (e.g. "ref", "ref2", etc.) are dropped
  * any instance of `+` is replaced with `_plus_` and `/` with `_over_`
  * all component names are converted to their "canonical names" when possible (e.g. "m1" in an EEG-matched channel name will be converted to "a1").

See the OndaEDF README for additional details regarding EDF formatting expectations.

!!! warning
    Returned samples are integer-encoded. If these samples are being serialized out (e.g. via `Onda.store!`) this is not an issue, but if the samples are being immediately analyzed in memory, call `Onda.decode` to decode them to recover the time-series voltages.

