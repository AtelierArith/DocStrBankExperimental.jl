difftime(time1::Union{DateTime, Missing}, time2::Union{DateTime, Missing}, units::AbstractString)

指定された単位で2つの時間の差を計算します。

# 引数

`time1`: DateTimeオブジェクト（DataFrame内に欠損値を含む可能性があります）。 `time2`: DateTimeオブジェクト（DataFrame内に欠損値を含む可能性があります）。 `units`: 2つの時間の差を計算する際に使用する単位を指定する文字列。単位は次のいずれかです: "seconds", "minutes", "hours", "days", "weeks"。

# 戻り値

指定された単位での2つの時間の差。入力のいずれかが欠損している場合、関数は欠損値を返します。

# 例

```jldoctest
julia> time1 = DateTime(2023, 6, 15, 9, 30, 0)
2023-06-15T09:30:00

julia> time2 = DateTime(2023, 6, 15, 8, 30, 0)
2023-06-15T08:30:00

julia> difftime(time1, time2, "hours")
1.0

julia> difftime(time1, time2, "minutes")
60.0

julia> difftime(time1, missing, "hours")
missing
```
