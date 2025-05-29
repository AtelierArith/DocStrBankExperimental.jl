```
decode!(result_storage, samples::Samples)
```

`samples.encoded`が`true`の場合、次のようにラップされた`Samples`インスタンスを返します。

```
decode!(result_storage, samples.info.sample_resolution_in_unit, samples.info.sample_offset_in_unit, samples.data)
```

`samples.encoded`が`false`の場合、`copyto!(result_storage, samples.data)`でラップされた`Samples`インスタンスを返します。
