```
ydn2md(year, day) -> date
```

### 目的

年と年の日数から日付に変換します。

### 説明

`year`の`day`に対応する日付を返します。

### 引数

  * `year`: 年を整数で指定します。
  * `day`: 年の中の日を整数で指定します。

### 出力

`year`の1月1日から$\text{day} - 1$日後の日付、`Date`型です。

### 例

2016年の60日目と234日目の日付を求めます。

```jldoctest
julia> using AstroLib

julia> ydn2md.(2016, [60, 234])
2-element Vector{Dates.Date}:
 2016-02-29
 2016-08-21
```

### 注意

`ymd2dn`は日付から年の日数に変換します。
