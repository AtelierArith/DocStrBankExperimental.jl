```
plan_edf_to_onda_samples(edf::EDF.File;
                         labels=STANDARD_LABELS,
                         units=STANDARD_UNITS,
                         extra_onda_signal_groupby=())
```

Formulate a plan for converting an `EDF.File` to Onda Samples.  This applies `plan_edf_to_onda_samples` to each individual signal contained in the file, storing `edf_signal_index` as an additional column.

The resulting rows are then passed to [`plan_edf_to_onda_samples_groups`](@ref) and grouped according to the `:sensor_type`, `:sample_unit`, and `:sample_rate` columns, as well as any additional columns specified in `extra_onda_signal_groupby`.  A `sensor_label` is generated for each group, based on the `sensor_type` but with a numeric suffix `_n` for the `n`th occurance of a `sensor_type` after the first.

The resulting plan is returned as a table.  No signal data is actually read from the EDF file; to execute this plan and generate `Onda.Samples`, use [`edf_to_onda_samples`](@ref).  The index of the EDF signal (after filtering out signals that are not `EDF.Signal`s, e.g. annotation channels) for each row is stored in the `:edf_signal_index` column, and the rows are sorted in order of `:sensor_label`, and then by `:edf_signal_index`.
