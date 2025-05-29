```
@kern function k(trace, args...)
    ...
end
```

Construct a composite MCMC kernel.

The resulting object is a Julia function that is annotated as a composite MCMC kernel, and can be called as a Julia function or applied within other composite kernels.
