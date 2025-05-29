```
MutableMemoryView(::Unsafe, x::MemoryView)
```

Convert a memory view into a mutable memory view. Note that it may cause undefined behaviour, if supposedly immutable data is observed to be mutated.
