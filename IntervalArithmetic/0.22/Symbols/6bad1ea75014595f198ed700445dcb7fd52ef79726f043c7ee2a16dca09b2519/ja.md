```
..(a, b)
a .. b
```

IEEE標準1788-2015に従って区間$[a, b]$を作成します。これは意味的に[`interval(a, b)`](@ref)と同等です。

!!! danger
    浮動小数点リテラルは解析時に最も近い値に丸められるため、その事実を補うための処理は行われません（例：`0.1`）。そのような場合は、希望する値を含む文字列を解析して、厳密な囲いを確保してください。


参照：[`interval`](@ref)、[`±`](@ref)および[`@I_str`](@ref)。

# 例

```jldoctest
julia> using IntervalArithmetic

julia> using IntervalArithmetic.Symbols

julia> setdisplay(:full);

julia> (1//1)..π
Interval{Rational{Int64}}(1//1, 85563208//27235615, com)

julia> 0.1..0.3
Interval{Float64}(0.1, 0.3, com)
```
