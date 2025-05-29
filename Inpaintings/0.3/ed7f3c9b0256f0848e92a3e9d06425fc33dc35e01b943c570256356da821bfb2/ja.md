```
inpaint(A, value_to_fill)
```

`value_to_fill` の値をインペイントします（`NaN` も可能です）。これは、データが欠損値を任意に選ばれた値で埋めることによって生成された場合に便利です。

# 例

```jldoctest
julia> A = float((1:3)*(1:4)') ; A[1:2, 1:2] .= 999 ; A
3×4 Array{Float64,2}:
 999.0  999.0  3.0   4.0
 999.0  999.0  6.0   8.0
   3.0    6.0  9.0  12.0

julia> inpaint(A, 999)
3×4 Array{Float64,2}:
 1.0  2.0  3.0   4.0
 2.0  4.0  6.0   8.0
 3.0  6.0  9.0  12.0
```

```jldoctest
julia> A = float((1:3)*(1:4)') ; A[1:2, 1:2] .= NaN ; A
3×4 Array{Float64,2}:
 NaN    NaN    3.0   4.0
 NaN    NaN    6.0   8.0
   3.0    6.0  9.0  12.0

julia> inpaint(A, NaN)
3×4 Array{Float64,2}:
 1.0  2.0  3.0   4.0
 2.0  4.0  6.0   8.0
 3.0  6.0  9.0  12.0
```
