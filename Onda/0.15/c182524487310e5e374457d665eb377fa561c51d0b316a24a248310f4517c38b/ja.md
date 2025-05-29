```
sizeof_samples(x, duration::Period)
```

`x`と`duration`に対応するエンコードされた`Samples`オブジェクトの期待されるサイズ（バイト単位）を返します：

```
sample_count(x, duration) * channel_count(x) * sizeof(x.sample_type)
```
