```
setdosetime!(data::DataSet{T}, dosetime::DoseTime, sort::Dict) where T <: AbstractSubject
```

Set dose time `dosetime` for subjects if `sort` ⊆ subject's `id`.
