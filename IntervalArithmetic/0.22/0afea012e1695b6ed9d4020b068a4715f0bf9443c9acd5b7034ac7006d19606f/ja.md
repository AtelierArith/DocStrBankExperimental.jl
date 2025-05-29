```
bareinterval(T, a, b)
```

IEEE標準1788-2015に従って、ベア区間$[a, b]$を作成します。区間の有効性は[`is_valid_interval`](@ref)によってチェックされます：`true`の場合、`BareInterval{T}`が構築され、それ以外の場合は空の区間が返されます。

!!! danger
    浮動小数点リテラルが解析時に最も近い値に丸められることを補うための処理は行われません（例：`0.1`）。そのような場合は、望ましい値を含む文字列を解析して、その厳密な囲いを確保してください。


関連情報: [`interval`](@ref), [`±`](@ref), [`..`](@ref) および [`@I_str`](@ref).

# 例

```jldoctest
julia> setdisplay(:full);

julia> bareinterval(1//1, π)
BareInterval{Rational{Int64}}(1//1, 85563208//27235615)

julia> bareinterval(Rational{Int32}, 1//1, π)
BareInterval{Rational{Int32}}(1//1, 85563208//27235615)

julia> bareinterval(1, π)
BareInterval{Float64}(1.0, 3.1415926535897936)

julia> bareinterval(BigFloat, 1, π)
BareInterval{BigFloat}(1.0, 3.141592653589793238462643383279502884197169399375105820974944592307816406286233)
```
