```
ReadStatColMeta <: AbstractMetaDict
```

A collection of variable-level metadata associated with a data column processed with `ReadStat`.

Metadata can be retrieved and modified from the associated [`ReadStatTable`](@ref) via methods compatible with `DataAPI.jl`. A dictionary-like interface is also available for directly working with `ReadStatColMeta`, but it does not allow modifying metadata values. An alternative way to retrive and modify the metadata is via [`colmetavalues`](@ref).

# Fields

  * `label::String`: variable label.
  * `format::String`: variable format.
  * `type::readstat_type_t`: original variable type recognized by `ReadStat`.
  * `vallabel::Symbol`: name of the dictionary of value labels associated with the variable; see also [`getvaluelabels`](@ref) for the effect of modifying this field.
  * `storage_width::Csize_t`: variable storage width in data file.
  * `display_width::Cint`: width for display.
  * `measure::readstat_measure_t`: measure type of the variable; only relevant to SPSS.
  * `alignment::readstat_alignment_t`: variable display alignment.
