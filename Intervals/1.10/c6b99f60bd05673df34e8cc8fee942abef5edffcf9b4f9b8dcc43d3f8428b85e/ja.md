```
HourEnding{T<:TimeType, L, R} <: AbstractInterval{T}
```

`AnchoredInterval{Hour(-1), T}` の型エイリアスであり、時間の瞬間（型 `T`）で終了する1時間の期間を示すために使用されます。

`HourEnding{T}` のインスタンスを構築する際、結果として得られる区間は右閉区間になります（型 `HourEnding{T,Open,Closed}`）。
