```
recursion_free(f::Function,args...)
```

creates a `Signal` whos action `f(args...)` is protected against infinite loop recursion.

```
julia> A = Signal(1)
julia> B = recursion_free(A) do a
            A(a+1)
       end

julia> A(10)
10
julia> A[]
11
```

In the example above ,if `recursion_free` were to be subsituted with regular `Signal` it would result in an infinite loop in the non-async mode `recursion_free` protects against that
