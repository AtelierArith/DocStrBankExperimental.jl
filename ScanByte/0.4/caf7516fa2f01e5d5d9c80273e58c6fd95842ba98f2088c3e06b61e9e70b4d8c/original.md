```
memchr(x, bytes)
memchr(ptr::Ptr, len::UInt, bytes)
```

Return first position of any byte in `bytes`, in memory `mem`, or `nothing` if no bytes were found

`bytes` can be a `Val{::ByteSet}`, in which case this function specializes  to the byteset, or a single `UInt8`, in which case it does not.

`x` can be any type that implements `pointer` and `sizeof`, or alternatively a pointer and a memory length can be passed.
