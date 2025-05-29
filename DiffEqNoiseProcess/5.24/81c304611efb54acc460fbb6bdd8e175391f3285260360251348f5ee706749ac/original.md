```julia
NoiseFunction{T, N, wType, zType, Tt, T2, T3, inplace} <:
AbstractNoiseProcess{T, N, nothing, inplace}
```

This allows you to use any arbitrary function `W(t)` as a `NoiseProcess`. This will use the function lazily, only caching values required to minimize function calls, but not storing the entire noise array. This requires an initial time point `t0` in the domain of `W`. A second function is needed if the desired SDE algorithm requires multiple processes.

```julia
NoiseFunction{iip}(t0, W, Z = nothing;
    noise_prototype = W(nothing, nothing, t0),
    reset = true) where {iip}
```

Additionally, one can use an in-place function `W(out1,out2,t)` for more efficient generation of the arrays for mulitidimensional processes. When the in-place version is used without a dispatch for the out-of-place version, the `noise_prototype` needs to be set.

## NoiseFunction Example

The `NoiseFunction` is pretty simple: pass a function. As a silly example, we can use `exp` as a noise process by doing:

```julia
f(u, p, t) = exp(t)
W = NoiseFunction(0.0, f)
```

If it's mulitidimensional and an in-place function is used, the `noise_prototype` must be given. For example:

```julia
f(out, u, p, t) = (out .= exp(t))
W = NoiseFunction(0.0, f, noise_prototype = rand(4))
```

This allows you to put arbitrarily weird noise into SDEs and RODEs. Have fun.
