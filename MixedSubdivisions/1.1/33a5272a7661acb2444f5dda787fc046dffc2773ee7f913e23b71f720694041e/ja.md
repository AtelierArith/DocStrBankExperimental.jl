```
mixed_cells(support::Vector{<:Matrix}, lifting::Vector{<:Vector})
```

与えられた `support` によって誘導されるすべての（細かい）混合セルを、与えられた `lifting` に基づいて計算します。リフティングが十分に一般的でない場合、わずかに摂動されたリフティングによって誘導される混合セルが計算されます。混合セルは [`MixedCell`](@ref) として保存されます。
