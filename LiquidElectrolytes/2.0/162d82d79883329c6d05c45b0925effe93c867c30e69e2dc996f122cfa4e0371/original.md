```
RLog(eps)
```

Callable struct for regularized  logarithm. Smooth linear continuation for `x<eps`. This means we can calculate a "logarithm"  of a small negative number. Objects `mylog::RLog`  of this type are meant to replace the logarithm function and allow to invoke `mylog(x)`.
