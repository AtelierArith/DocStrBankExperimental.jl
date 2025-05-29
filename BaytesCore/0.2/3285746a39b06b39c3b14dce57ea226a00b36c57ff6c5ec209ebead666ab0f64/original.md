```julia
struct DataTune{D<:BaytesCore.DataStructure, C<:Union{Nothing, BaytesCore.ArrayConfig}, M}
```

Data tuning struct.

Contains information about data structure.

# Fields

  * `structure::BaytesCore.DataStructure`: Subtype of DataStructure
  * `config::Union{Nothing, BaytesCore.ArrayConfig}`: Data dimension configuration.
  * `miss::Any`: Treatment of missing data.
