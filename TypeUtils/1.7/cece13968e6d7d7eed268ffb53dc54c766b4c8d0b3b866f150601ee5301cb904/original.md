```
is_signed(::T)
is_signed(T::Type)
```

yield whether a number of type `T` can be negated while retaining the same type. `false` is returned for `T <: Union{U,Rational{U},Complex{U}} where {U<:Union{Bool,Unsigned}}` as well as quantities based on these bare numeric types.
