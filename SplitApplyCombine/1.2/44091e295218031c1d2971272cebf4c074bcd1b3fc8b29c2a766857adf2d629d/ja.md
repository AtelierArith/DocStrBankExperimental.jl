```
mapview(f, a)
```

`a`のビューを返し、各要素は関数`f`を通してマッピングされます。`a`の反復およびインデックスの特性は保持されます。`map(f, a)`に似ていますが、遅延評価されます。

# 例

```julia
julia> a = [1,2,3];

julia> b = mapview(-, a)
3-element MappedArray{Int64,1,typeof(-),Array{Int64,1}}:
 -1
 -2
 -3

julia> a[1] = 10;

julia> b
3-element MappedArray{Int64,1,typeof(-),Array{Int64,1}}:
 -10
  -2
  -3
```
