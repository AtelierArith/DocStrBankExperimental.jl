```julia
ConvertOrdinalDate(num::DPart, from::String, to::String)
```

`num` は序数日であり、すなわちカレンダーの紀元の始まりから経過した日数をカウントする整数です。

`from` と `to` は序数日名です。現在、許可されている序数日名は「EuroNum」と「JulianNum」、それぞれの略称は EN と JN です。

例: ジュリアン日数をヨーロッパ日数に変換します。

```julia
julia> ConvertOrdinalDate(2440422, JN, EN) 
```

有人月面着陸のヨーロッパ日数は 719000 です。

ヨーロッパ日数をジュリアン日数に変換します。

```julia
julia> ConvertOrdinalDate(719000, EN, JN) 
```

有人月面着陸のジュリアン日数は 2440422 です。
