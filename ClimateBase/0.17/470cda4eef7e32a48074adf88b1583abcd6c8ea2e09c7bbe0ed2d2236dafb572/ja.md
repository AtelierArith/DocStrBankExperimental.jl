```
maxyearspan(A::ClimArray) = maxyearspan(dims(A, Time))
maxyearspan(t::AbstractVector{<:DateTime}) → i
```

`t`の最大インデックス `i` を見つけます。これにより、`t[1:i]` が正確な(*) 年の倍数をカバーします。

(*) 月間データの場合、`i` は `12` の倍数であり、日次データの場合は `DAYS_IN_ORBIT` の最大の倍数を見つけます。
