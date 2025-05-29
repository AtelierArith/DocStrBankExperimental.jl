```
setbl!(data::DataSet{T}, bl, sort::Dict) where T <: PDSubject
```

Set `baseline` only for subjects which `sort` ⊆ `id` is `true`.
