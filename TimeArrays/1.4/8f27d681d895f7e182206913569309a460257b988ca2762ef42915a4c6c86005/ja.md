```
ta_sma(t_array::TimeArray, n::Integer; kw...) -> TimeArray
ta_sma(t_array::TimeArray, p::Period; kw...) -> TimeArray
```

`t_array`の要素に対して、ウィンドウサイズ`n`または期間`p`を用いた[単純移動平均](https://en.wikipedia.org/wiki/Moving_average)アルゴリズムを適用します。

## キーワード引数

  * 詳細については[`ta_rolling`](@ref)を参照してください。

## 例

```jldoctest
julia> using Dates

julia> t_array = TimeArray([
           TimeTick(DateTime("2024-01-02"), 1.0),
           TimeTick(DateTime("2024-01-03"), 2.0),
           TimeTick(DateTime("2024-01-05"), 3.0),
           TimeTick(DateTime("2024-01-06"), 4.0),
           TimeTick(DateTime("2024-01-09"), 5.0),
       ]);

julia> ta_sma(t_array, 2)
5-element TimeArray{DateTime, Float64}:
 TimeTick(2024-01-02T00:00:00, NaN)
 TimeTick(2024-01-03T00:00:00, 1.5)
 TimeTick(2024-01-05T00:00:00, 2.5)
 TimeTick(2024-01-06T00:00:00, 3.5)
 TimeTick(2024-01-09T00:00:00, 4.5)

julia> t_array = TimeArray([
           TimeTick(DateTime("2024-01-02"), 1.0),
           TimeTick(DateTime("2024-01-03"), 2.0),
           TimeTick(DateTime("2024-01-05"), 3.0),
           TimeTick(DateTime("2024-01-06"), 4.0),
           TimeTick(DateTime("2024-01-09"), 5.0),
       ]);

julia> ta_sma(t_array, Day(3))
5-element TimeArray{DateTime, Float64}:
 TimeTick(2024-01-02T00:00:00, NaN)
 TimeTick(2024-01-03T00:00:00, 1.5)
 TimeTick(2024-01-05T00:00:00, 2.5)
 TimeTick(2024-01-06T00:00:00, 3.5)
 TimeTick(2024-01-09T00:00:00, 5.0)
```
