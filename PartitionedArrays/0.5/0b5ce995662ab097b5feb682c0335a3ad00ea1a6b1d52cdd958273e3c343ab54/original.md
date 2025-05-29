```
pvector([f,]I,V,index_partition;kwargs...) -> Task
```

Crate an instance of [`PVector`](@ref) by setting arbitrary entries from each of the underlying parts. It returns a task that produces the instance of [`PVector`](@ref) allowing latency hiding while performing the communications needed in its setup.
