```
struct GEM{T <: Union{DataFrame, OrderedDict{String, OrderedDict{String, Any}}}}
```

Represents a **General Equivalence Map (GEM)** table.

# FIELDS

  * `data<: Union{DataFrame,OrderedDict{String, OrderedDict{String, Any}}}`: the actual GEM data, as returned by `get_gem_dataframe_from_cdc_gem_txt` or `get_GEM_dictionary_from_cdc_gem_txt`, so it may be a `DataFrame` or an `OrderedDict`;
  * `direction::String`: either `"I9_I10"` (from ICD-9 to ICD-10) or `"I10_I9"` (from ICD-10 to ICD-9).
