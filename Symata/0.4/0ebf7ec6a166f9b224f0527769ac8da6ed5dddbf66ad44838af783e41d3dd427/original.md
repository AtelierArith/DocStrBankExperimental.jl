```
setpart!(mx::Mxpr,val,inds...)
```

set the part of `mx` indexed by `inds` to `val`.

The last index equal to zero means the head of the subexpression specified by the previous indices. Because most heads are effectively immutable, we must replace the final subexpression in this case.
