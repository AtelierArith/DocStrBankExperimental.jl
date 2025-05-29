```
fits_zero_offset(T::Type)
```

線形スケーリング方程式で使用されるゼロオフセット `a`

```
f(x) = a + b x,
```

ここで `b` はスケーリングファクターです。

デフォルト値は `Real` 数値型に対して `a = 0.0` です。非実数型の場合、`a = nothing` です。

#### 例:

```
julia> T = Type[Any, Bool, Int8, UInt8, Int16, UInt16, Int32, UInt32,
                  Int64, UInt64, Float16, Float32, Float64];

julia> o = (0.0, 0.0, -128, 0.0, 0.0, 32768,
                   0.0, 2147483648, 0.0, 9223372036854775808, 0.0, 0.0, 0.0);

julia> sum([fits_zero_offset(T[i]) == o[i] for i ∈ eachindex(T)]) == 13
true
```
