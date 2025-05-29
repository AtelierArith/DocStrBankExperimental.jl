```
sample_type(x)
```

Return `x.sample_type` as an `Onda.LPCM_SAMPLE_TYPE_UNION` subtype. If `x.sample_type` is an Onda-specified `sample_type` string (e.g. `"int16"`), it will be converted to the corresponding Julia type. If `x.sample_type <: Onda.LPCM_SAMPLE_TYPE_UNION`, this function simply returns `x.sample_type` as-is.
