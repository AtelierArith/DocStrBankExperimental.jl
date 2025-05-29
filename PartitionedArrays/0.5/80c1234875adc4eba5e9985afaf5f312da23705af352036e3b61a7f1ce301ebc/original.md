```
rewind_ptrs(a)!
```

Sets `a[i+1]=a[i]` for `i in (length(a)-1):-1:1` and then `a[1] = one(eltype(a))`.
