```
decode(samples::Samples, ::Type{T}=Float64)
```

`samples.encoded`が`true`の場合、次のようにラップされた`Samples`インスタンスを返します。

```
decode(convert(T, samples.info.sample_resolution_in_unit),
       convert(T, samples.info.sample_offset_in_unit),
       samples.data)
```

`samples.encoded`が`false`の場合、この関数は恒等関数です。
