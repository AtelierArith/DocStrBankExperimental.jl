```
add_values(values::Vector{Float64}, indices::Vector{Int64}, increments::Vector{Float64})
```

`increments`の値を`values`の`indices`で指定された現在の値に加えます。境界チェックやベクトルの長さの整合性は行いません。この関数を呼び出す前に行う必要があります。
