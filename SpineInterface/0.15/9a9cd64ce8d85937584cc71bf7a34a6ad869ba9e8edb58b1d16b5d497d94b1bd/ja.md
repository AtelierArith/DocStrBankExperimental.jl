```
roll!(t::TimeSlice, forward::Union{Period,CompoundPeriod})
```

指定された`forward`の期間だけ`t`を時間的にロールし、呼び出しの更新を返します。
