```
 data = loadragged(ncvar,index::Union{Colon,UnitRange,Integer})
```

`ncvar`から[連続したラグド配列表現](https://web.archive.org/web/20190111092546/http://cfconventions.org/cf-conventions/v1.6.0/cf-conventions.html#_contiguous_ragged_array_representation)としてベクトルのベクトルをロードします。これは通常、異なる長さのプロファイルまたは時系列のリストをロードするために使用されます。

[インデックス付きラグド配列表現](https://web.archive.org/web/20190111092546/http://cfconventions.org/cf-conventions/v1.6.0/cf-conventions.html#_indexed_ragged_array_representation)は現在サポートされていません。
