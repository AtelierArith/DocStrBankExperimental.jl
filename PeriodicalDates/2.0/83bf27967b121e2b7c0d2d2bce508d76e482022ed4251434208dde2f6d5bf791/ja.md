QuarterlyDate(d::AbstractString, format::AbstractString; locale="english") -> QuarterlyDate

指定された`format`文字列に従って日付文字列を解析することによって、日付を構築します。

このメソッドは呼び出されるたびに`DateFormat`オブジェクトを作成します。同じ形式の多くの日付文字列を解析する場合は、`DateFormat`オブジェクトを一度作成し、それを第二引数として使用することを検討してください。

### 例

```julia
julia> QuarterlyDate("1990-01", "yyy-mm")
julia> QuarterlyDate("1990-Q1", "yyy-Qq")
```
