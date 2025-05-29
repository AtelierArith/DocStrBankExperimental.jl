```julia
isregular(timestamps::V, unit::T) where {V<:AbstractVector{TimeType}, T<:Dates.Period}
isregular(timestamps::T) where {T<:AbstractVector{TimeType}}
isregular(timestamps::AbstractVector{V}, unit::Symbol = :firstdiff) where {V<:TimeType}
isregular(ts::TSFrame, unit::Symbol = :firstdiff)
isregular(ts::TSFrame, unit::T) where {T<:Dates.Period}
```

tsが規則的かどうかを確認します。

  * unit == :firstdiff の場合、インデックスの最初の差が一定であるかどうかを確認します。
  * そうでない場合、指定された時間期間に関して最初の差が一定であるかどうかを確認します。

例えば、unit == :month の場合、月に関して最初の差が一定であるかどうかを確認します。

# 例

```jldoctest; setup = :(using TSFrame, Dates, Random)
julia> using Random;
julia> random(x) = rand(MersenneTwister(123), x);

julia> dates=collect(Date(2017,1,1):Day(1):Date(2017,1,10))
10-element Vector{Date}:
 2017-01-01
 2017-01-02
 2017-01-03
 2017-01-04
 2017-01-05
 2017-01-06
 2017-01-07
 2017-01-08
 2017-01-09
 2017-01-10

julia> isregular(dates) # 規則的かどうかを確認
true

julia> isregular(dates, Day(1)) # 1日の時間差で規則的かどうかを確認
true

julia> isregular(dates, Day(2)) # 2日の時間差で規則的かどうかを確認
false

julia> isregular(dates, :month) # 月に関して規則的かどうかを確認
false

julia> ts = TSFrame(random(10), dates)
10×1 TSFrame with Date Index
 Index       x1        
 Date        Float64   
───────────────────────
 2017-01-01  0.768448
 2017-01-02  0.940515
 2017-01-03  0.673959
 2017-01-04  0.395453
 2017-01-05  0.313244
 2017-01-06  0.662555
 2017-01-07  0.586022
 2017-01-08  0.0521332
 2017-01-09  0.26864
 2017-01-10  0.108871

julia> isregular(ts)
true

julia> isregular(ts, Day(1))
true

julia> isregular(ts, Day(2))
false

julia> isregular(ts, :month)
false
```
