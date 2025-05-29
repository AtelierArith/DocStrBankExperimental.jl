```
encode!(result_storage, sample_type::DataType, sample_resolution_in_unit,
        sample_offset_in_unit, sample_data, dither_storage=nothing)
encode!(result_storage, sample_resolution_in_unit, sample_offset_in_unit,
        sample_data, dither_storage=nothing)
```

Similar to `encode(sample_type, sample_resolution_in_unit, sample_offset_in_unit, sample_data, dither_storage)`, but write encoded values to `result_storage` rather than allocating new storage.

`sample_type` defaults to `eltype(result_storage)` if it is not provided.

If:

```
sample_type === eltype(sample_data) &&
sample_resolution_in_unit == 1 &&
sample_offset_in_unit == 0
```

then this function will simply copy `sample_data` directly into `result_storage` without dithering.
