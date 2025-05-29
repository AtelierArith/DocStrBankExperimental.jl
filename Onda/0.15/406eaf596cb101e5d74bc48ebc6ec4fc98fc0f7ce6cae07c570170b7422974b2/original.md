```
decode!(result_storage, samples::Samples)
```

If `samples.encoded` is `true`, return a `Samples` instance that wraps

```
decode!(result_storage, samples.info.sample_resolution_in_unit, samples.info.sample_offset_in_unit, samples.data)
```

If `samples.encoded` is `false`, return a `Samples` instance that wraps `copyto!(result_storage, samples.data)`.
