```
decode(sample_resolution_in_unit, sample_offset_in_unit, sample_data)
```

`fma.(sample_resolution_in_unit, sample_data, sample_offset_in_unit)`を返します。

もし:

```
sample_data isa AbstractArray &&
sample_resolution_in_unit == 1 &&
sample_offset_in_unit == 0
```

であれば、この関数は恒等関数であり、`sample_data`を直接コピーせずに返します。
