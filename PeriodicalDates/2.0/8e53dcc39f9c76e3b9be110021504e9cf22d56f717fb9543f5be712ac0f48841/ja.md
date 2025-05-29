YearlyDate(d::AbstractString, format::AbstractString; locale="english") -> YearlyDate

指定された`format`文字列に従って日付文字列を解析することによってDateを構築します。

このメソッドは呼び出されるたびに`DateFormat`オブジェクトを作成します。同じ形式の多くの日付文字列を解析する場合は、一度`DateFormat`オブジェクトを作成し、それを第二引数として使用することを検討してください。

### 例

```julia
julia> YearlyDate("1990-01", "yyy-mm")
julia> YearlyDate("1990-Q1", "yyy-Qq")
```
