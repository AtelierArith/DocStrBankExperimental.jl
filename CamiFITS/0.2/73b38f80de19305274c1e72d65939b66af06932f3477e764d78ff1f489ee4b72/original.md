```
fits_zero_offset(T::Type)
```

Zero offset `a` as used in linear scaling equation

```
f(x) = a + b x,
```

where `b` is the scaling factor. 

The default value is `a = 0.0` for `Real` numeric types.  For non-real types `a = nothing`.

#### Example:

```
julia> T = Type[Any, Bool, Int8, UInt8, Int16, UInt16, Int32, UInt32,
                  Int64, UInt64, Float16, Float32, Float64];

julia> o = (0.0, 0.0, -128, 0.0, 0.0, 32768,
                   0.0, 2147483648, 0.0, 9223372036854775808, 0.0, 0.0, 0.0);

julia> sum([fits_zero_offset(T[i]) == o[i] for i ∈ eachindex(T)]) == 13
true
```
