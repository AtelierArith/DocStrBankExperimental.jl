```
check_allocs!(system,true_or_false)
```

Enable/disable checking for time-consuming allocations in the assembly loop.  By default,  this check  is switched off.  By setting  the environment variable `ENV["VORONOIFVM_CHECK_ALLOCS"]="true"`, this  default can be changed.

Unless  the   matrix  pattern  changes,  there   shouldn't  occur  any allocations in this loop. The check  method is aware of matrix pattern changes. As a consequence, allocations in the assembly loop are mostly due to type instabilities in physics callbacks, see the the discussion [here](../runexamples/#Performance-with-closures).  Type instabilities can be debugged via the `@time`  macro applied to expressions in a physics callback.

The following  cases provide some ideas  where to look for  reasons of the problem and possible remedies:

Case 1: a parameter changes its value, and Julia is not sure about the type.

```julia
eps=1.0

flux(f,_u,edge)
    u=unkowns(edge,_u)
    f[1]=eps*(u[1,1]-[1,2])
end
... solve etc ...
eps=2.0
```

Remedy: use a type annotation `eps::Float64=...` to signalize your intent to Julia. This behaviour is explained in the [Julia documentation](https://docs.julialang.org/en/v1/manual/performance-tips/#man-performance-captured).

Case 2: variables in the closure have the same name as a variable introduced in a callback.

```julia
flux(f,_u,edge)
    u=unkowns(edge,_u)
    f[1]=(u[1,1]-[1,2])
end

... create etc ...

u=solve(...)
```

Remedy: rename e.g. `u=solve()` to `sol=solve()`
