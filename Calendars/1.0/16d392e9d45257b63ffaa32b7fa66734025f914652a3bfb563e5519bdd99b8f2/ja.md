```julia
DayOfYear(date::CDate)
```

指定されたカレンダーにおける日の序数を返します。カレンダーのエポックに対する「序数日」としても知られています。

```julia
julia> DayOfYear(EC, 1756, 1, 27) 
```

また、次のように書くこともできます。

```julia
julia> DayOfYear("European", 1756,  1, 27) 
```

出力から、EC-1756-01-27はヨーロッパのカレンダーにおける1756年の27日目であることがわかります。同じ日はヘブライカレンダーでは年の144日目になります：

`julia julia> DayOfYear(ConvertDate(EC, 1756, 1, 27, AM))`

エラーが発生した場合、0（無効な年の日を表す）が返されます。
