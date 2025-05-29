```
DDNOut(x::Symbol)
DDNOut{x::Symbol}()
DDNOut(::Symbol, ::Symbol,...)
DDNOut{x::NTuple{N, Symbol}}()
```

Reference to one or more named nodes in the POMDP or MDP dynamic decision network (DDN).

`DDNOut` is a "value type". See [the documentation of `Val`](https://docs.julialang.org/en/v1/manual/types/index.html#%22Value-types%22-1) for more conceptual details about value types.
