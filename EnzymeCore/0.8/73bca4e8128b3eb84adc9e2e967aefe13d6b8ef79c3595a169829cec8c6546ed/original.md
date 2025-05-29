```
make_zero(::Type{T}, seen::IdDict, prev::T, ::Val{copy_if_inactive}=Val(false))::T
```

Recursively make a zero'd copy of the value `prev` of type `T`. The argument `copy_if_inactive` specifies what to do if the type `T` is guaranteed to be inactive, use the primal (the default) or still copy the value. 
