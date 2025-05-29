```
TimeArray{T,V}(values::AbstractVector)
```

`values` から `TimeArrays{T,V}` を作成します。この `values` には [`TimeTick{T,V}`](@ref TimeTick) コンストラクタに渡すことができる任意の要素が含まれています。

!!! warning
    このアプローチはパフォーマンスを大幅に低下させます。自己の裁量で使用してください。


## 例

```jldoctest
julia> using Dates

julia> values = [
           TimeTick(Date("2024-01-02"), 3.0),
           (DateTime("2024-01-03"), 1.0),
           Date("2024-01-01") => 2,
       ];

julia> TimeArray{Date,Int64}(values)
3-element TimeArray{Date, Int64}:
 TimeTick(2024-01-01, 2)
 TimeTick(2024-01-02, 3)
 TimeTick(2024-01-03, 1)
```
