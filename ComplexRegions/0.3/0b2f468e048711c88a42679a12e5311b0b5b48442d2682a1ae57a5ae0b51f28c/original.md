```
normal(P::AbstractPath,t::Real)
```

Compute a complex-valued normal to path `P` at parameter value `t`. Values of `t` in [k,k+1] correspond to values in [0,1] along curve k of the path, for k = 1,2,...,length(P)-1. The result is not well-defined at an integer value of `t`.
