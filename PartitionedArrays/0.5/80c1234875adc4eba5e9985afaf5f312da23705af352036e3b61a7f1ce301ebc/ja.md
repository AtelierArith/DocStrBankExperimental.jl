```
rewind_ptrs(a)!
```

`a[i+1]=a[i]` を `i in (length(a)-1):-1:1` の範囲で設定し、その後 `a[1] = one(eltype(a))` を設定します。
