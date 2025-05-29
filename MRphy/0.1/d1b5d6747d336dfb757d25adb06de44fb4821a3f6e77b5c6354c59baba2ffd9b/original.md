```
TypeND(T,Ns) = Union{AbstractArray{<:T,Ns[1]}, AbstractArray{<:T,Ns[2]},...}
```

Sugar for creating `Union`{`<:T` typed array of different dimensions}.

# Usage

*INPUTS*:

  * `T::Type` (1,), the underlying type of the union.
  * `Ns::Array{Int64,1}` (# diff dims,), an array of wanted dimensions.
