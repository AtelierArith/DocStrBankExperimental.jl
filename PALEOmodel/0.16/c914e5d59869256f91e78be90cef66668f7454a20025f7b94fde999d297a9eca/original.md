```
FieldRecord(dataset, avalues::Array, avalues_dimnames, attributes::Dict{Symbol, Any}; [expand_cartesian=false])
```

Create from an Array of data values `avalues`.

FieldRecord type and dimensions are set from a combination of `attributes` and `dataset` dimensions and grid, where `Space = attributes[:space]`, `FieldData = attributes[:field_data]`, `data_dims` are set from names in `attributes[:data_dims]`.

Dimension names and size are cross-checked against supplied names in `avalues_dimnames`

This is effectively the inverse of:

```
a = FieldArray(
    fr::FieldRecord;
    lookup_coords=false, omit_recorddim_if_constant=true, expand_cartesian=true,
)
avalues = a.values
avalues_dimnames = [nd.name for (nd, _) in a.dims_coords]
attributes = a.attributes
```
