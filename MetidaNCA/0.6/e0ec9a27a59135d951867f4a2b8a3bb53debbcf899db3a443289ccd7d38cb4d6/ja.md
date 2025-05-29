```
setdosetime!(data::DataSet{T}, dosetime::DoseTime, sort::Dict) where T <: AbstractSubject
```

被験者の `id` に対して `sort` ⊆ の場合、被験者のために投与時間 `dosetime` を設定します。
