```
AttractivenessSpatIndex{T <: AbstractMetaPOI}(filename::AbstractString, get_range::Function=get_attractiveness_range, get_group::Function=get_attractiveness_group)
AttractivenessSpatIndex{T <: AbstractMetaPOI}(df::AbstractDataFrame, get_range::Function=get_attractiveness_range, get_group::Function=get_attractiveness_group)
```

Builds an attractivness spatial index basing on data in some CSV file or a DataFrame

Assuming that `T` is of typw `AttractivenessMetaPOI`,  the CSV file or DataFrame should have the following columns:     - group - data group in attractiveness index, each group name creates attractiveness dimension     - key - key in the XML file <tag>     - values - values in the <tag> (a star `"*"` catches all values)     - influence - strength of influence     - range - maximum influence range in meters

When a `DataFrame` is provided the additional parameter `refLLA` can be provided for the reference `LLA` coordinates in the spatial index. The spatial index works in the ENU coordinate system.

If `T` is not provided `AttractivenessMetaPOI` will be used as the default metadata type.

The type `F` represents the attractiveness group function provided as  `get_group = (a::T) -> :somegroup`.
