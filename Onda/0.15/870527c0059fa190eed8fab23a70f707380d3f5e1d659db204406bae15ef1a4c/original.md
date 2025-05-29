```
encode(samples::Samples, dither_storage=nothing)
```

If `samples.encoded` is `false`, return a `Samples` instance that wraps:

```
encode(sample_type(samples.info),
       samples.info.sample_resolution_in_unit,
       samples.info.sample_offset_in_unit,
       samples.data, dither_storage)
```

If `samples.encoded` is `true`, this function is the identity.
