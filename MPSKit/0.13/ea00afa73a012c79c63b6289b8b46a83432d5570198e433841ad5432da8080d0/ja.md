```
correlation_length(above::InfiniteMPS; kwargs...)
```

与えられたInfiniteMPSの相関長を、転送行列の次位の固有値に基づいて計算します。`kwargs`は[`transfer_spectrum`](@ref)に渡され、特定のセクターでの相関長をターゲットにするために使用できます。
