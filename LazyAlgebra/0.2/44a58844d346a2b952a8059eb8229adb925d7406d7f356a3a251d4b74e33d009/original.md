```
vmul!(y, A, x) -> y
```

overwrites `y` with the result of `A*x` and returns `y`. The default behavior is to call `apply!(1,Direct,A,x,false,0,y)`.

!!! note
    This method is intended to be used by algorithms such as the conjugate gradient to apply operators. It may be specialized by the caller for its needs which is much easier than specializing [`apply!`](@ref) which requires to consider the specific values of the multipliers `α` and `β`.

