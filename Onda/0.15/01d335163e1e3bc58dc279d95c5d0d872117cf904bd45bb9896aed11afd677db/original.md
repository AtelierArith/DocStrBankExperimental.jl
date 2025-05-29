```
decode(sample_resolution_in_unit, sample_offset_in_unit, sample_data)
```

Return `fma.(sample_resolution_in_unit, sample_data, sample_offset_in_unit)`.

If:

```
sample_data isa AbstractArray &&
sample_resolution_in_unit == 1 &&
sample_offset_in_unit == 0
```

then this function is the identity and will return `sample_data` directly without copying.
