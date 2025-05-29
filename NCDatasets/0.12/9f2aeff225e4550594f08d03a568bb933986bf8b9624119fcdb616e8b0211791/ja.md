```
defDim(ds::NCDataset,name,len)
```

データセット `ds` に指定された `name` と長さ `len` で次元を定義します。`len` が特別な値 `Inf` の場合、その次元は `unlimited` と見なされ、NetCDFファイルにデータが追加されるにつれて成長します。

例えば：

```julia
using NCDatasets
ds = NCDataset("/tmp/test.nc","c")
defDim(ds,"lon",100)
# [...]
close(ds)
```

これはサイズ100の次元 `lon` を定義します。

無制限の次元を持つ変数を作成するには、例えば次のようにします：

```julia
using NCDatasets
ds = NCDataset("/tmp/test2.nc","c")
defDim(ds,"lon",10)
defDim(ds,"lat",10)
defDim(ds,"time",Inf)
defVar(ds,"unlimited_variable",Float64,("lon","lat","time"))
@show ds.dim["time"]
# データが追加されていないため、0を返します
ds["unlimited_variable"][:,:,:] = randn(10,10,4)
@show ds.dim["time"]
# 4つの時間スライスが追加されたため、今は4を返します
close(ds)
```
