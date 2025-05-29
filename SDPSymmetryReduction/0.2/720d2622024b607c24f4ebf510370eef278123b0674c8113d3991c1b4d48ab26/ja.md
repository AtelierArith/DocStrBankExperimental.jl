```
dim(ap::AbstractPartition)
```

パーティション部分空間 `ap` の次元。

# !!! 注

# `0`-集合（最初のサブセット）は特別な意味を持ち、計算には含まれません。

# 例

```julia
julia> q = SR.Partition(Float64[
           1 1 0;
           1 0 5;
           0 3 3
       ]);

julia> SR.dim(q)
3

julia> p = SR.Partition([
           1 1 2;
           1 2 5;
           2 3 3
       ]);

julia> SR.dim(p)
4

```
