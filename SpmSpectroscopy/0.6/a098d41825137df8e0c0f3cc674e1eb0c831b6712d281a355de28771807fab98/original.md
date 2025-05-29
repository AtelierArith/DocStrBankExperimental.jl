```
load_spectrum(filename::AbstractString; select::AbstractVector=Bool[], header_only::Bool=false, remove_missing::Bool=false,
    index_column::Bool=false, index_column_type::Type=Int)::SpmSpectrum
```

Loads a spectrum from the file `filename`. Currently, only Nanonis .dat files are supported. `select` can be used to specify which columns to load (see CSV.jl for an explanation of `select`). If `header_only` is `true`, then only the header is loaded. If `index_column` is `true`, then an extra column with indices of type `index_column_type` will be added. If `remove_missing` is `true`, then missing values are dropped.
