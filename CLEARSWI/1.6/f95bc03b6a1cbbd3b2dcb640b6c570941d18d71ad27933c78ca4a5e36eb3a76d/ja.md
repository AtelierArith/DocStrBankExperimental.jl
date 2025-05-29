```
createMIP(S::AbstractArray{<:Number,3}, d=7)
```

`S`の最小強度投影を`d`スライスで作成します。

# 例

```julia-repl
julia> TEs = [4,8,12]
julia> data = Data(mag, phase, header(mag), TEs);
julia> swi = calculateSWI(data);
julia> mip = createMIP(swi);
```

関連項目 [`createIntensityProjection`](@ref)
