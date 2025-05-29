```
extract(
    odata :: AbstractArray{<:Real},
    ggrd  :: UnstructuredGrid
) -> Array{<:Real}
```

親 `GeoRegion` のデータを含む配列 `odata` から、私たちが興味のあるサブ `GeoRegion` 内のデータのみを含む次元 N の別の配列に抽出します。

!!! warning
    続行する前に、1 次元が経度で 2 次元が緯度であることを確認してください。ただし、3 次元目と 4 次元目の順序（使用する場合）は重要ではありません。


# 引数

  * `odata` : 抽出する地域におけるグリッドデータを含む次元 N の配列
  * `ggrd` : 抽出する内容に関する詳細情報を含む `RegionGrid`
