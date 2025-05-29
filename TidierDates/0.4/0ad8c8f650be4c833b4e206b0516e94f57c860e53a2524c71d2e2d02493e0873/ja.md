```
floor_date(dt::Union{DateTime, Missing}, unit::String)
```

DateTimeオブジェクトを指定された単位に切り下げます。

# 引数

`dt`: DateTimeオブジェクト（DataFrame内に欠損値を含むことがあります）。 `unit`: 切り下げに使用する単位を指定する文字列。単位は次のいずれかです: "year", "quarter", "month", "week", "day", "hour", "minute"。

# 戻り値

指定された単位に切り下げられたDateTimeオブジェクト。入力が欠損している場合、関数は欠損値を返します。

"week"単位を使用する場合、日曜日が週の最初の日と見なされ、日付がすでに日曜日である場合はそのまま返されます。

# 例

```jldoctest
julia> dt = DateTime(2023, 6, 15, 9, 45)
2023-06-15T09:45:00

julia> floor_date(dt, "hour")
2023-06-15T09:00:00

julia> floor_date(dt, "day")
2023-06-15T00:00:00

julia> floor_date(dt, "week")
2023-06-11T00:00:00

julia> floor_date(dt, "quarter")
2023-04-01T00:00:00

julia> floor_date(missing, "day")
missing
```
