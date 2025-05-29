```
Tensor(lvl, [undef], dims...)
```

Construct a `Tensor` of size `dims`, and initialize to `undef`, potentially allocating memory.  Here `undef` is the `UndefInitializer` singleton type. `dims...` may be a variable number of dimensions or a tuple of dimensions, but it must correspond to the number of dimensions in `lvl`.
