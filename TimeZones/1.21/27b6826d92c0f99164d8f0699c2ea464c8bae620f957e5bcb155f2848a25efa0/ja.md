```
all_timezones(criteria::Function) -> Vector{TimeZone}
```

指定された `criteria` 関数に一致する `TimeZone` を返します。`criteria` 関数は2つのパラメータを取ります：UTCの遷移（`DateTime`）と遷移ゾーン（`FixedTimeZone`）です。

## 例

絶対UTCオフセットが15時間を超えるすべてのタイムゾーンを見つけます：

```julia
all_timezones() do dt, zone
    abs(zone.offset.std) > Dates.Second(Dates.Hour(15))
end
```

非時間単位の夏時間オフセットを持つすべてのタイムゾーンを特定します：

```julia
all_timezones() do dt, zone
    zone.offset.dst % Dates.Second(Dates.Hour(1)) != 0
end
```
