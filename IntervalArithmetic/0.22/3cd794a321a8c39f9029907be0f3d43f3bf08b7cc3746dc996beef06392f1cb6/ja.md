```
interval(T, a, b, d = com)
```

IEEE標準1788-2015に従って区間$[a, b]$を作成します。区間の有効性は[`is_valid_interval`](@ref)によってチェックされます：`true`の場合は`Interval{T}`が構築され、それ以外の場合はNaI（Not an Interval）が返されます。

!!! danger
    浮動小数点リテラルが解析時に最も近い値に丸められることを補うための処理は行われません（例：`0.1`）。そのような場合は、希望する値を含む文字列を解析して、その厳密な囲いを確保してください。


参照：[`±`](@ref)、[`..`](@ref)および[`@I_str`](@ref)。

# 例

```jldoctest
julia> setdisplay(:full);

julia> interval(1//1, π)
Interval{Rational{Int64}}(1//1, 85563208//27235615, com)

julia> interval(Rational{Int32}, 1//1, π)
Interval{Rational{Int32}}(1//1, 85563208//27235615, com)

julia> interval(1, π)
Interval{Float64}(1.0, 3.1415926535897936, com)

julia> interval(BigFloat, 1, π)
Interval{BigFloat}(1.0, 3.141592653589793238462643383279502884197169399375105820974944592307816406286233, com)
```
