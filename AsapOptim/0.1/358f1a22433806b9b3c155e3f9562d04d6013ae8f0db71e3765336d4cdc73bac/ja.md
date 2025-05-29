```
replace_values(values::Vector{Float64}, indices::Vector{Int64}, newvalues::Vector{Float64})
```

`values[indices]`の値を`newvalues`の値で置き換えます。微分可能な方法で行います。境界チェックやベクトルの長さの整合性は行いません。この関数を呼び出す前に行う必要があります。
