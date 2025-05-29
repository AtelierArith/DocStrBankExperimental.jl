```
encode!(result_storage, samples::Samples, dither_storage=nothing)
```

`samples.encoded`が`false`の場合、次のようにラップされた`Samples`インスタンスを返します：

```
encode!(result_storage,
        sample_type(samples.info),
        samples.info.sample_resolution_in_unit,
        samples.info.sample_offset_in_unit,
        samples.data, dither_storage)`.
```

`samples.encoded`が`true`の場合、`copyto!(result_storage, samples.data)`でラップされた`Samples`インスタンスを返します。
