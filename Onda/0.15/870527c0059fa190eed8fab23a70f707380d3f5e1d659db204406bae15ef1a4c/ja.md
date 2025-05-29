```
encode(samples::Samples, dither_storage=nothing)
```

`samples.encoded` が `false` の場合、次のようにラップされた `Samples` インスタンスを返します：

```
encode(sample_type(samples.info),
       samples.info.sample_resolution_in_unit,
       samples.info.sample_offset_in_unit,
       samples.data, dither_storage)
```

`samples.encoded` が `true` の場合、この関数は恒等関数です。
