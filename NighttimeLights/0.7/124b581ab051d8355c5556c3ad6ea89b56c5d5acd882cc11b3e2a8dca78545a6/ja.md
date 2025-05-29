マスクに存在するデータキューブの各時系列に関数を適用します。

# 例:

```
julia> datacube = rand(1:10.0, 10,10,10)
julia> mask = rand(0:1, 10, 10)
julia> iterator(x::Vector) = x .+ 1
julia> long_apply(x, datacube)
```
