```
reset!{T<:DeferredRemoteRef}(ref::T) -> T
```

Removes any data from the `DeferredRemoteRef` and allows it to be reinitialized with data.

Returns the input `DeferredRemoteRef`.
