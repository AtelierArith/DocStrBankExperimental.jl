```
AlignedSpan(sample_rate, span, mode::RoundingModeFullyContainedSampleSpans)
```

入力スパンに含まれる各サンプルから次のサンプルが発生するまでの完全なスパンで構成される`AlignedSpan`を構築します。

例えば：

```jldoctest
julia> using TimeSpans, AlignedSpans, Dates

julia> sample_rate = 1/30
0.03333333333333333

julia> input = TimeSpan(0, Second(30) + Nanosecond(1))
TimeSpan(00:00:00.000000000, 00:00:30.000000001)

julia> aligned = AlignedSpan(sample_rate, input, RoundFullyContainedSampleSpans)
AlignedSpan(0.03333333333333333, 1, 1)

julia> TimeSpan(aligned)
TimeSpan(00:00:00.000000000, 00:00:30.000000000)
```

ここでは、[`RoundInward`](@ref)や[`RoundSpanDown`](@ref)の動作とは対照的に、入力スパンに完全に含まれる30秒の「サンプルスパン」が1つだけであるため、1つのサンプルのみが含まれます。
