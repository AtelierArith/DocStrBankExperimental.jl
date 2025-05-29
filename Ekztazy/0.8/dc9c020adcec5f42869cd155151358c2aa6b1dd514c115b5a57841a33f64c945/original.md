```
fetchval(f::Future{Response{T}}) -> Nullable{T}
```

Shortcut for `fetch(f).val`: Fetch a [`Response`](@ref) and return its value. Note that there are no guarantees about the response's success and the value being returned, and it discards context that can be useful for debugging, such as HTTP responses and caught exceptions.
