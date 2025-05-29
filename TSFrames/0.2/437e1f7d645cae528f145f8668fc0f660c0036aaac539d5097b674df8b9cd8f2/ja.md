# エンドポイントの計算

```julia
endpoints(timestamps::AbstractVector{T}, on::V) where {T<:Union{Date, DateTime, Time}, V<:Dates.Period}
endpoints(ts::TSFrame, on::T) where {T<:Dates.Period}
endpoints(ts::TSFrame, on::Symbol, k::Int=1)
endpoints(ts::TSFrame, on::String, k::Int=1)
endpoints(ts::TSFrame, on::Function, k::Int=1)
endpoints(values::AbstractVector, on::Function, k::Int=1)
```

`timestamps` の各期間に対する最後の観測値の整数ベクトルを返します。値は、期間の `on.value` インスタンスごとに選択されます。

この関数の戻り値を使用して、`TSFrame` オブジェクトを直接サブセットすることができます。メソッドは、`Dates` モジュールによって提供される任意の時間ベースの型に属する、任意の周期性の通常の時系列および不規則な時系列に対して機能します。

主要なメソッドは、`Date`、`DateTime`、および `Time` を含むすべての時間型の系列に対して機能し、`on` は `Dates.Period` の任意のサブタイプに属します。`::TSFrame` メソッドは便利のために提供されており、`Index` 列を使用して主要なメソッドを直接呼び出します。

`Function` 型の `on` を受け入れるメソッドでは、`values` ベクトルがユニークな期間グループに変換され、ユニークなキーとして機能します。このメソッドは、これらのキーを使用して値のグループを作成し、`on` によって提供された期間を使用して各グループの最後の観測値を選択します。`k` はスキップするグループの数を決定します。たとえば、`k=2` は、`on` によって作成された要素のうち、2番目の要素から始まるすべての交互のグループを選択します。以下の例を参照して、関数が実際の世界でどのように機能するかを確認してください。`on` 関数は、グループ化キーとして使用される `Vector` を返す必要があります。

`endpoints(ts::TSFrame, on::Symbol)` および `endpoints(ts::TSFrame, on::String)` は便利なメソッドであり、`on` の有効な値は次のとおりです: `:years`, `:quarters`, `:months`, `:weeks`, `:days`, `:hours`, `:minutes`, `:seconds`, `:milliseconds`, `:microseconds`, および `:nanoseconds`。

`on::Function` を除いて、他のすべてのメソッドは、`TSFrame` の `Index` 型が `TimeType` のサブタイプであることを期待します。

このメソッドは、最初の引数に対応する `Vector{Int}` を返します。

# 例

```jldoctest; setup = :(using TSFrames, DataFrames, Dates, Random, Statistics)
julia> using Random
julia> random(x) = rand(MersenneTwister(123), x);
julia> dates = Date(2017):Day(1):Date(2019);
julia> ts = TSFrame(random(length(dates)), dates)
(731 x 1) TSFrame with Date Index

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
     ⋮           ⋮
 2018-12-24  0.812797
 2018-12-25  0.158056
 2018-12-26  0.269285
 2018-12-27  0.15065
 2018-12-28  0.916177
 2018-12-29  0.278016
 2018-12-30  0.617211
 2018-12-31  0.67549
 2019-01-01  0.910285
       712 rows omitted

julia> ep = endpoints(ts, Month(1))
25-element Vector{Int64}:
  31
  59
  90
 120
 151
 181
 212
 243
 273
 304
 334
 365
 396
 424
 455
 485
 516
 546
 577
 608
 638
 669
 699
 730
 731

julia> ts[ep]
(25 x 1) TSFrame with Date Index

 Index       x1
 Date        Float64
───────────────────────
 2017-01-31  0.48
 2017-02-28  0.458476
 2017-03-31  0.274441
 2017-04-30  0.413966
 2017-05-31  0.734931
 2017-06-30  0.257159
 2017-07-31  0.415851
 2017-08-31  0.0377973
 2017-09-30  0.934059
 2017-10-31  0.413175
 2017-11-30  0.557009
 2017-12-31  0.346659
 2018-01-31  0.174777
 2018-02-28  0.432223
 2018-03-31  0.835142
 2018-04-30  0.945539
 2018-05-31  0.0635483
 2018-06-30  0.589922
 2018-07-31  0.285088
 2018-08-31  0.912558
 2018-09-30  0.238931
 2018-10-31  0.49775
 2018-11-30  0.830232
 2018-12-31  0.67549
 2019-01-01  0.910285

julia> diff(index(ts[ep]))
24-element Vector{Day}:
 28 days
 31 days
 30 days
 31 days
 30 days
 31 days
 31 days
 30 days
 31 days
 30 days
 31 days
 31 days
 28 days
 31 days
 30 days
 31 days
 30 days
 31 days
 31 days
 30 days
 31 days
 30 days
 31 days
 1 day

# 毎月2ⁿᵈ
julia> ts[endpoints(ts, Month(2))]
(12 x 1) TSFrame with Date Index

 Index       x1
 Date        Float64
───────────────────────
 2017-02-28  0.458476
 2017-04-30  0.413966
 2017-06-30  0.257159
 2017-08-31  0.0377973
 2017-10-31  0.413175
 2017-12-31  0.346659
 2018-02-28  0.432223
 2018-04-30  0.945539
 2018-06-30  0.589922
 2018-08-31  0.912558
 2018-10-31  0.49775
 2018-12-31  0.67549
 2019-01-01  0.910285

# 関数を使用した週次ポイント
julia> endpoints(ts, i -> lastdayofweek.(i), 1)
106-element Vector{Int64}:
   1
   8
  15
  22
  29
  36
  43
   ⋮
 694
 701
 708
 715
 722
 729
 731

julia> endpoints(ts, i -> lastdayofweek.(i), 1) == endpoints(ts, Week(1))
true

# 時間型系列
julia> timestampsminutes = collect(Time(9, 1, 2):Minute(1):Time(11, 2, 3));
julia> timestampsminutes[endpoints(timestampsminutes, Minute(2))]
61-element Vector{Time}:
 09:02:02
 09:04:02
 09:06:02
 09:08:02
 09:10:02
 09:12:02
 09:14:02
 09:16:02
 09:18:02
 09:20:02
 09:22:02
 09:24:02
 ⋮
 10:40:02
 10:42:02
 10:44:02
 10:46:02
 10:48:02
 10:50:02
 10:52:02
 10:54:02
 10:56:02
 10:58:02
 11:00:02
 11:02:02

julia> timestampsminutes[endpoints(timestampsminutes, Hour(1))]
3-element Vector{Time}:
 09:59:02
 10:59:02
 11:02:02

## 不規則な系列
julia> datetimeseconds = collect(range(DateTime(2022, 10, 08) + Hour(9),
                                DateTime(2022, 10, 08) + Hour(15) + Minute(29),
                                step=Second(1)));
julia> datetimesecondsrandom = sample(MersenneTwister(123), datetimeseconds, 20, replace=false, ordered=true)
17-element Vector{DateTime}:
 2022-10-08T09:20:16
 2022-10-08T09:32:00
 2022-10-08T09:43:57
 2022-10-08T10:13:27
 2022-10-08T10:44:34
 2022-10-08T11:04:23
 2022-10-08T11:08:37
 2022-10-08T11:46:51
 2022-10-08T11:56:46
 2022-10-08T12:14:22
 2022-10-08T12:32:08
 2022-10-08T13:28:42
 2022-10-08T13:34:33
 2022-10-08T13:54:11
 2022-10-08T13:59:08
 2022-10-08T14:05:57
 2022-10-08T14:37:17

julia> datetimesecondsrandom[endpoints(datetimesecondsrandom, Hour(1))]
6-element Vector{DateTime}:
 2022-10-08T09:43:57
 2022-10-08T10:44:34
 2022-10-08T11:56:46
 2022-10-08T12:32:08
 2022-10-08T13:59:08
 2022-10-08T14:37:17
```
