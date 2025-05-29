```
timestamp(deps::Union{PyObject, <:Real, Missing}=missing)
```

These functions are usually used with [`bind`](@ref) for profiling.  Note the timing is not very accurate in a multithreaded environment.

  * `deps`: `deps` is always executed before returning the timestamp.

# Example

```julia
a = constant(3.0)
t0 = timestamp(a)
sleep_time = sleep_for(a)
t1 = timestamp(sleep_time)
sess = Session(); init(sess)
t0_, t1_ = run(sess, [t0, t1])
time = t1_ - t0_
```
