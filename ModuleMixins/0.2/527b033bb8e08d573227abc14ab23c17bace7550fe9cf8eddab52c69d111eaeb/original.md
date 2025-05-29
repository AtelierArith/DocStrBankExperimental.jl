```
@for_each(M -> M.method(), lst::Vector{Symbol})
```

Calls `method()` for each module in `lst` that actually implements that method. Here `lst` should be a vector of symbols that are all in the current module's namespace.
