```julia
now(T)
```

は、エポックからの現在の時間を型 `T` のインスタンスとして返します。`T` は [`TimeVal`](@ref) または [`TimeSpec`](@ref) であることができます。

関連情報: [`gettimeofday`](@ref),  [`time`](@ref),  [`clock_gettime`](@ref).
