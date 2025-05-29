```
encode(sample_type::DataType, sample_resolution_in_unit, sample_offset_in_unit,
       sample_data, dither_storage=nothing)
```

Return a copy of `sample_data` quantized according to `sample_type`, `sample_resolution_in_unit`, and `sample_offset_in_unit`. `sample_type` must be a concrete subtype of `Onda.LPCM_SAMPLE_TYPE_UNION`. Quantization of an individual sample `s` is performed via:

```
round(S, (s - sample_offset_in_unit) / sample_resolution_in_unit)
```

with additional special casing to clip values exceeding the encoding's dynamic range.

If `dither_storage isa Nothing`, no dithering is applied before quantization.

If `dither_storage isa Missing`, dither storage is allocated automatically and triangular dithering is applied to the info prior to quantization.

Otherwise, `dither_storage` must be a container of similar shape and type to `sample_data`. This container is then used to store the random noise needed for the triangular dithering process, which is applied to the info prior to quantization.

If:

```
sample_type === eltype(sample_data) &&
sample_resolution_in_unit == 1 &&
sample_offset_in_unit == 0
```

then this function will simply return `sample_data` directly without copying/dithering.
