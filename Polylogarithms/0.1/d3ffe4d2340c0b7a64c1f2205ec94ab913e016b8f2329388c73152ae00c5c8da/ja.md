```
harmonic(x::ComplexOrReal{Float64})
```

非整数引数に拡張された調和数をディガンマ形式を使用して計算します。

## 引数

  * $$
    x
    $$

    `::ComplexOrReal{Float64}`: 計算する調和数のインデックス

## 例

```jldoctest; setup = :(using Polylogarithms)
julia> harmonic(2.0)
1.5000000000000016
```
