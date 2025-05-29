```
VTKDataArray(xml_element, vtk_file)
```

指定された `xml_element` と対応する `vtk_file` のための軽量コンテナを作成します。

`xml_element` は `DataArray` 型でなければならず、`vtk_file` パラメータは実際のデータを取得するために必要です。実際のデータを取得するには、`get_data` に `VTKDataArray` オブジェクトを渡すことができます。

参照: [`get_data`](@ref)
