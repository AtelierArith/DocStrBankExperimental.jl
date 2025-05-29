```
FieldRecord(dataset, avalues::Array, avalues_dimnames, attributes::Dict{Symbol, Any}; [expand_cartesian=false])
```

データ値の配列 `avalues` から作成します。

FieldRecord 型と次元は、`attributes` と `dataset` の次元およびグリッドの組み合わせから設定されます。ここで、`Space = attributes[:space]`、`FieldData = attributes[:field_data]`、`data_dims` は `attributes[:data_dims]` の名前から設定されます。

次元名とサイズは、`avalues_dimnames` に提供された名前と照合されます。

これは実質的に次の逆です：

```
a = FieldArray(
    fr::FieldRecord;
    lookup_coords=false, omit_recorddim_if_constant=true, expand_cartesian=true,
)
avalues = a.values
avalues_dimnames = [nd.name for (nd, _) in a.dims_coords]
attributes = a.attributes
```
