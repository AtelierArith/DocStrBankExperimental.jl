```
compress(A::CategoricalArray)
```

Return a copy of categorical array `A` using the smallest reference type able to hold the number of [`levels`](@ref DataAPI.levels) of `A`.

While this will reduce memory use, this function is type-unstable, which can affect performance inside the function where the call is made. Therefore, use it with caution.
