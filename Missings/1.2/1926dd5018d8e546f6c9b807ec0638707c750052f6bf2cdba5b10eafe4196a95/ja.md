```
disallowmissing(x::AbstractArray)
```

`missing`[@ref] 値を許可しない `x` と等しい配列を返します。すなわち、要素の型は `nonmissingtype(eltype(x))` になります。

可能な場合、結果は `x` とメモリを共有します（[`convert`](@ref) のように）。`x` に `missing` 値が含まれている場合、`MethodError` がスローされます。

関連情報: [`allowmissing`](@ref)
