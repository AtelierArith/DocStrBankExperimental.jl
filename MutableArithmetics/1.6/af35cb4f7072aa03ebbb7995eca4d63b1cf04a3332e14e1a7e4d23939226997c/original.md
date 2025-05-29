```
struct IsMutable <: MutableTrait end
```

When this is returned by [`mutability`](@ref), it means that object of the given type can always be mutated to equal the result of the operation.
