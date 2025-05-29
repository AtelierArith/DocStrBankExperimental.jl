```
QCDNUM.save_params(file_name::String, params::Union{EvolutionParams,SPLINTParams})
QCDNUM.save_params(::Type{HDF5.File}, file_name::String, params::Union{EvolutionParams,SPLINTParams})
QCDNUM.save_params(trg::HDF5.H5DataStore, params::Union{EvolutionParams,SPLINTParams})
```

Store the QCDNUM or SPLINT parameters for reproducibility.
