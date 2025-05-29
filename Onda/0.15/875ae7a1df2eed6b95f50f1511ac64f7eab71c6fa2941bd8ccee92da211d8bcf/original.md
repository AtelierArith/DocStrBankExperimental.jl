```
decode(samples::Samples, ::Type{T}=Float64)
```

If `samples.encoded` is `true`, return a `Samples` instance that wraps

```
decode(convert(T, samples.info.sample_resolution_in_unit),
       convert(T, samples.info.sample_offset_in_unit),
       samples.data)
```

If `samples.encoded` is `false`, this function is the identity.
