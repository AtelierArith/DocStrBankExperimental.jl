```
getallvalues(v::AbstractThreadLocal{T})::AbstractVector{T}
```

Access the all values (one for each thread) of a thread-local value as a vector. Can only be called in single-threaded code sections.
