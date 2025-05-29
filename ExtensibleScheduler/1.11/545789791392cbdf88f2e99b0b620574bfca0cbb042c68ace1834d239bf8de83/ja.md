```
iterate(trigger, dt[, n=number_of_times])
```

インスタント `dt` からトリガーを使用して、指定された反復回数 `n` で反復します。 `n < 0` の場合（デフォルトは `-1`）、無限に反復します。

# 使用法

```
julia> trigger = Trigger(Dates.Time(20, 30))

julia> for dt in iterate(trigger, DateTime(2020, 1, 1), n=3)
         @show dt
       end
dt = 2020-01-01T20:30:00
dt = 2020-01-02T20:30:00
dt = 2020-01-03T20:30:00

julia> collect(iterate(trigger, DateTime(2020, 1, 1), n=3))
3-element Array{Any,1}:
 2020-01-01T20:30:00
 2020-01-02T20:30:00
 2020-01-03T20:30:00
```
