```
convert_to_dataset(obj; group = :posterior, kwargs...) -> Dataset
```

サポートされているオブジェクトを `Dataset` に変換します。

ほとんどの場合、この関数は [`convert_to_inference_data`](@ref) を呼び出し、対応する `group` を返します。
