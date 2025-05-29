```
update!(m::MutableModel, table)
```

Update the model in-place from an object that implements the Tables.jl interface.

Note: the parent object can be immutable, it will be completely rebuilt.  But the wrapper `AbstractModel` is mutable, such as `Model` or `InteractModel`.
