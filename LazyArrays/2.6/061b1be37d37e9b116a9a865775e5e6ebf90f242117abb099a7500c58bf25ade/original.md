```
LazyArray(x::Applied) :: ApplyArray
LazyArray(x::Broadcasted) :: BroadcastArray
```

Wrap a lazy object that wraps a computation producing an array to an array.
