```
encode!(result_storage, sample_type::DataType, sample_resolution_in_unit,
        sample_offset_in_unit, sample_data, dither_storage=nothing)
encode!(result_storage, sample_resolution_in_unit, sample_offset_in_unit,
        sample_data, dither_storage=nothing)
```

`encode(sample_type, sample_resolution_in_unit, sample_offset_in_unit, sample_data, dither_storage)`と似ていますが、新しいストレージを割り当てるのではなく、`result_storage`にエンコードされた値を書き込みます。

`sample_type`は提供されていない場合、`eltype(result_storage)`がデフォルトになります。

もし：

```
sample_type === eltype(sample_data) &&
sample_resolution_in_unit == 1 &&
sample_offset_in_unit == 0
```

であれば、この関数は単に`sample_data`をditheringなしで`result_storage`に直接コピーします。
