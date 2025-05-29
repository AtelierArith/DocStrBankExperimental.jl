```
getindex(plan::RecoPlan{T}, name::Symbol) where {T}
```

`plan`の`name`プロパティの`Observable`を返します。`plan[name]`と同等です。
