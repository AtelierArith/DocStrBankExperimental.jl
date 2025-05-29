```
Trace(A::AbstractArray)
```

Similar to [`Slices`](https://github.com/JuliaLang/julia/blob/master/base/slicearray.jl) which will be introduced in `Julia@v1.9`. The main difference is that, the `axes` info in the `Slices` is static, while it may be dynamic with `Trace`.

We only support slices along the last dimension since it's the most common usage in RL.
