```
allowmissing(x::AbstractArray)
```

`x`と等しい配列を返し、[`missing`](@ref) 値を許可します。つまり、要素の型は `Union{eltype(x), Missing}` になります。

可能な場合、結果は `x` とメモリを共有します（[`convert`](@ref) のように）。

関連情報: [`disallowmissing`](@ref)
