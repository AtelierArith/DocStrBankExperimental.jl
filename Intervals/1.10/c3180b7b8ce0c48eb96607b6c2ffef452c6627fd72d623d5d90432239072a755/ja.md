```
HourBeginning{T<:TimeType, L, R} <: AbstractInterval{T}
```

`AnchoredInterval{Hour(1), T}`の型エイリアスであり、時間の瞬間（型`T`）で始まる1時間の期間を示すために使用されます。

`HourBeginning{T}`のインスタンスを構築する際、結果として得られる区間は左閉じ（型`HourBeginning{T,Closed,Open}`）になります。
