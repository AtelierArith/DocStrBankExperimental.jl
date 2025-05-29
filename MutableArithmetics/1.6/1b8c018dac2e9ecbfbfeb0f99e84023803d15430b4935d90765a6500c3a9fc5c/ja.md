```
broadcast_mutability(T::Type, ::typeof(op), args::Type...)::MutableTrait
```

`IsMutable`を返して、型`T`のオブジェクトが`broadcast(op, args...)`と等しくなるように変更できることを示します。
