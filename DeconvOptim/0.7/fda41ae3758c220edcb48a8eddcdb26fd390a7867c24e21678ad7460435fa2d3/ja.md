```
center_set!(arr_large, arr_small)
```

`arr_small`を`arr_large`の中央に配置します。中央の位置は、FFTに基づく中心の定義と同じです。この関数は、偶数および奇数の配列の両方で機能します。

# 例

```jldoctest
julia> DeconvOptim.center_set!([1, 1, 1, 1, 1, 1], [5, 5, 5])
6-element Array{Int64,1}:
 1
 1
 5
 5
 5
 1
```
