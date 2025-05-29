```
realtime_days(t::AbstractVector{<:TimeType}, T = Float32)
```

与えられた*連続的*な日時ベクトル`t`を「実時間」の形式のベクトルに変換します。ここで時間は実数で表され、累積的に増加します。これは、時系列`x(t)`を表す場合と同様です。この形式では差分のみが重要であるため、返されるベクトルは常に0から始まります。ここでの時間の測定単位は日です。

日単位未満の時間サンプリングの場合は、`realtime_milliseconds(t) ./ (24*60*60*1000)`を返します。

例:

```juliarepl
julia> t = Date(2004):Month(1):Date(2004, 6)
Date("2004-01-01"):Month(1):Date("2004-06-01")

julia> realtime_days(t)
6-element Vector{Float32}:
   0.0
  29.0
  60.0
  90.0
 121.0
 151.0
```
