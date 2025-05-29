```
ThreadSafeDict(pairs::Vector{Pair{K,V}})
```

Struct and constructor for ThreadSafeDict. There is one lock per Dict struct. All functions lock this lock, pass  arguments to the d member Dict, unlock the spinlock, and then return what is returned by the Dict.
