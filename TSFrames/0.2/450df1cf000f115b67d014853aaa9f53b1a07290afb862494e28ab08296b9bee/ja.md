# ラグ

```julia
lag(ts::TSFrame, lag_value::Int = 1)
```

指定された `lag_value` によって `ts` オブジェクトをラグします。ラグされた値に対応する行は `missing` として表示されます。ラグの負の値も受け付けられます（`TSFrames.lead` を参照）。

# 例

```jldoctest; setup = :(using TSFrames, DataFrames, Dates, Random, Statistics)
julia> using Random, Statistics;

julia> random(x) = rand(MersenneTwister(123), x);

julia> dates = collect(Date(2017,1,1):Day(1):Date(2017,1,10));

julia> ts = TSFrame(random(length(dates)), dates);
julia> show(ts)
(10 x 1) TSFrame with Dates.Date Index

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


julia> lag(ts)
(10 x 1) TSFrame with Date Index

 Index       x1
 Date        Float64?
─────────────────────────────
 2017-01-01  missing
 2017-01-02        0.768448
 2017-01-03        0.940515
 2017-01-04        0.673959
 2017-01-05        0.395453
 2017-01-06        0.313244
 2017-01-07        0.662555
 2017-01-08        0.586022
 2017-01-09        0.0521332
 2017-01-10        0.26864

julia> lag(ts, 2) # 2つの値でラグ
(10 x 1) TSFrame with Date Index

 Index       x1
 Date        Float64?
─────────────────────────────
 2017-01-01  missing
 2017-01-02  missing
 2017-01-03        0.768448
 2017-01-04        0.940515
 2017-01-05        0.673959
 2017-01-06        0.395453
 2017-01-07        0.313244
 2017-01-08        0.662555
 2017-01-09        0.586022
 2017-01-10        0.0521332

```
