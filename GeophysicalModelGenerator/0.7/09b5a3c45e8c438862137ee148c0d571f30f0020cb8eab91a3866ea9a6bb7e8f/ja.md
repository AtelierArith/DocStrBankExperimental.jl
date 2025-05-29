```
V_sub = subtract_horizontalmean(V::AbstractArray{T, 2}; Percentage=false)
```

2Dデータ配列Vの水平平均を引きます。

`Percentage=true`の場合、結果はパーセンテージで返されます。それ以外の場合は絶対値が返されます。
