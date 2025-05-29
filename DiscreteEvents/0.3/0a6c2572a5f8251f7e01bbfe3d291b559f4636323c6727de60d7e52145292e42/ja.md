```
setUnit!(clk::Clock, new::FreeUnits)
```

`Unitful`で新しい時間単位に時計を設定します。必要に応じて、現在の時計の時間を新しい単位に変換します。

# 引数

  * `clk::Clock`
  * `new::FreeUnits`: newは`ms`、`s`、`minute`、`hr`または他のUnitful `Time`単位のいずれかです。

# 例

```jldoctest
julia> using DiscreteEvents, Unitful

julia> import Unitful: Time, s, minute, hr

julia> c = Clock(t0=60)     # t0=60で新しい時計を設定
Clock 1: state=:idle, t=60.0, Δt=0.01, prc:0
  scheduled ev:0, cev:0, sampl:0

julia> tau(c)               # 現在の時間は60.0 NoUnits
60.0

julia> setUnit!(c, s)       # 時計の単位をUnitful.sに設定
60.0 s

julia> tau(c)               # 現在の時間は60.0 sになりました
60.0 s

julia> setUnit!(c, minute)  # 時計の単位をUnitful.minuteに設定
1.0 minute

julia> tau(c)               # 現在の時間は1.0 minuteになりました
1.0 minute

julia> isa(tau(c), Time)
true

julia> uconvert(s, tau(c))  # ... 他の時間単位に変換できます
60.0 s

julia> tau(c).val           # 値は1.0です
1.0

julia> c.time               # 内部時計の時間は1.0（Float64）に設定されています
1.0

julia> c.unit               # 内部時計の単位はUnitful.minuteに設定されています
minute
```
