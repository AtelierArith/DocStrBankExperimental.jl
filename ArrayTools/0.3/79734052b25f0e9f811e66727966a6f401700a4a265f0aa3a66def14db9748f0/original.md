```
strictmap!(f, dst, src) -> dst
strictmap!(dst, f, src) -> dst
```

does `dst[i] = f(src[i])` for all indices `i` and returns `dst`. Arguments `dst` and `src` must have the same axes.

Except for the strict condition on the axes, this method is similar to `map!(f,dst,src)`.
