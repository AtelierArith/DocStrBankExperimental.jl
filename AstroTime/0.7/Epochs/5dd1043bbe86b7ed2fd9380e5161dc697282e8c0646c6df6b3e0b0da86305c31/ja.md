```
getoffset(TDB, TT, second, fraction[, eop])
```

[`TDB`](@ref) と [`TT`](@ref) の現在のエポック（J2000 からの `second` と `fraction`）におけるオフセットを秒単位で返します。このルーチンは、1900年から2100年の間で約40マイクロ秒の精度があります。

!!! note
    TDB と TT の正確な変換は、観測者の軌道に依存します。地球の表面に固定された2つの観測者の場合、TDB-TT の量は最大で約4マイクロ秒異なる可能性があります。詳細は [`here`](@ref getoffset(::BarycentricDynamicalTime, ::TerrestrialTime, second, fraction, elong, u, v)) を参照してください。


# 例

```jldoctest; setup = :(using AstroTime)
julia> getoffset(TDB, TT, 0, 0.0)
7.273677616693264e-5
```

### 参考文献

  * [https://www.cv.nrao.edu/~rfisher/Ephemerides/times.html#TDB](https://www.cv.nrao.edu/~rfisher/Ephemerides/times.html#TDB)
  * [Issue #26](https://github.com/JuliaAstro/AstroTime.jl/issues/26)

```
