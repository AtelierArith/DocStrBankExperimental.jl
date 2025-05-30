```
period(::Type{<:Period}, year::Integer, subperiod::Integer = 1)
```

年、サブ期間、および頻度から期間を構築します。

これらの期間は、[`ExtendedDates.epoch`](@ref) 関数によって定義されたエポックからの期間の Int64 数として表されます。ほとんどの期間タイプにとって、エポックは西暦0年1月1日土曜日です。週の期間にとっては、西暦0年1月3日月曜日です。

```jldoctest
julia> x = period(Semester, 2022, 1)
2022-S1

julia> Dates.format(x)
"2022-S1"

julia> Date(x)
2022-01-01

julia> Date(period(Week, 0))
0000-01-03

julia> Date(period(Day, 0))
0000-01-01
```
