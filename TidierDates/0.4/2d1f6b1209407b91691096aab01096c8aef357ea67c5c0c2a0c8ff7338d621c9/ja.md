```
round_date(dt::Union{DateTime, Date, Time, Missing}, unit::String)
```

DateTime、Date、またはTimeオブジェクトを指定された単位に最も近い値に丸めます。

# 引数

`dt`: DateTime、Date、またはTimeオブジェクト（DataFrame内に欠損値を含むことがあります）。 `unit`: 丸めに使用する単位を指定する文字列。単位は次のいずれかである必要があります: "year"、"quarter"、"month"、"day"、"hour"、"minute"、"second"。

# 戻り値

指定された単位に最も近い値に丸められたDateTime、Date、またはTimeオブジェクト。入力が欠損している場合、関数は欠損値を返します。

# 例

```jldoctest
julia> dt = DateTime(2023, 6, 15, 9, 45)
2023-06-15T09:45:00

julia> round_date(dt, "hour")
2023-06-15T10:00:00

julia> round_date(dt, "day")
2023-06-15T00:00:00

julia> round_date(dt, "quarter")
2023-07-01T00:00:00

julia> round_date(missing, "day")
missing
```
