```
getlocalvalue(x::Any) = x
getlocalvalue(x::ThreadLocal) = x[]
```

Access plain values and thread-local values in a unified fashion.
