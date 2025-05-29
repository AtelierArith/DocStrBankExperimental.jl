```
broadcast_mutability(T::Type, ::typeof(op), args::Type...)::MutableTrait
```

Return `IsMutable` to indicate an object of type `T` can be modified to be equal to `broadcast(op, args...)`.
