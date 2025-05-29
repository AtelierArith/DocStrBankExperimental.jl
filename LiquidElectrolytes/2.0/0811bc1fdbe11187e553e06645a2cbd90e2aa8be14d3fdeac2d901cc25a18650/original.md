```
RExp(trunc)
```

Callable struct for regularized exponential. Linear continuation for `x>trunc`,   returns 1/rexp(-x) for `x<-trunc`. Objects `myexp::RExp`  of this type are meant to replace the exponential function and allow to invoke `myexp(x)`.
