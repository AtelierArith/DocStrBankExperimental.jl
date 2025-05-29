```
plan_edf_to_onda_samples_groups(plan_rows; extra_onda_signal_groupby=())
```

Group together `plan_rows` based on the values of the `:sensor_type`, `:sample_unit`, `:sample_rate`, and `extra_onda_signal_groupby` columns, creating a unique `:sensor_label` per group and and promoting the Onda encodings for each group using [`OndaEDF.promote_encodings`](@ref).  All rows with the same `:sensor_label` will be combined into a single Onda Samples by [`edf_to_onda_samples`](@ref).

If the `:edf_signal_index` column is not present or otherwise missing, it will be filled in based on the order of the input rows.

The updated rows are returned, sorted first by the grouping columns and second by order of occurrence within the input rows.
