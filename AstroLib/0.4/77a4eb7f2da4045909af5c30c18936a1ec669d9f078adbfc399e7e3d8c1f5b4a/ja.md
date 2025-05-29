```
ymd2dn(date) -> number_of_days
```

### 目的

日付を年の日に変換します。

### 説明

`date` の年の日を返します。1月1日が1日目です。

### 引数

  * `date`: `Date` 型の日付。単一の日付または日付の配列であることができます。

### 出力

指定された `date` の年の日。`date` が配列の場合、日数の配列を返します。

### 例

2015年と2016年の3月5日の年の日を求めます（これはうるう年です）。

```jldoctest
julia> using AstroLib, Dates

julia> ymd2dn.([Date(2015, 3, 5), Date(2016, 3, 5)])
2-element Vector{Int64}:
 64
 65
```

### 注意

`ydn2md` は年と年の日数から日付に変換します。
