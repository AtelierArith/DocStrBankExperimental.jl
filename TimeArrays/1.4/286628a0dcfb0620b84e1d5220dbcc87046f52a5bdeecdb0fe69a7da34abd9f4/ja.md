```
ta_resample(f::Function, t_array::TimeArray{T,V}, period::PeriodLike; kw...) -> TimeArray
```

`t_array`の値を新しい`period`の新しい時間グリッドに移動し、古いグリッドの中間値に対して関数`f`を使用します。

関数`f`は、型`V`の要素を持つベクトルを入力として受け取り、新しい値を返す必要があります。この新しい値は、各ウィンドウの対応するタイムスタンプに割り当てられます。受け取ったベクトルに基づいて新しい値を計算することが不可能な場合（例えば、ベクトルが空の場合）、`NaN`値または同等の値（カスタム型の場合）を返す必要があります。

## キーワード引数

  * `origin::ORIGIN_TYPE = ORIGIN_OF_WINDOW`: 新しいグリッドの開始（可能な値: `ORIGIN_OF_WINDOW`, `START_OF_WINDOW`, `END_OF_WINDOW`）。
  * `closed::CLOSED_SIDE = CLOSED_LEFT`: 新しいグリッドの半開区間の閉じた側（可能な値: `CLOSED_LEFT`, `CLOSED_RIGHT`）。
  * `label::LABEL_SIDE = LABEL_LEFT`: 新しいグリッドの区間のラベル側（可能な値: `LABEL_LEFT`, `LABEL_RIGHT`）。

詳細については[`resample section`](@ref resample)を参照してください。

## 例

```jldoctest
julia> t_array = TimeArray{Int64,Int64}([(i, i) for i in 3:13])
11-element TimeArray{Int64, Int64}:
 TimeTick(3, 3)
 TimeTick(4, 4)
 TimeTick(5, 5)
 TimeTick(6, 6)
 TimeTick(7, 7)
 TimeTick(8, 8)
 TimeTick(9, 9)
 TimeTick(10, 10)
 TimeTick(11, 11)
 TimeTick(12, 12)
 TimeTick(13, 13)

julia> ta_resample(sum, t_array, 4, closed = CLOSED_LEFT, label = LABEL_LEFT)
4-element TimeArray{Int64, Int64}:
 TimeTick(0, 3)
 TimeTick(4, 22)
 TimeTick(8, 38)
 TimeTick(12, 25)

julia> ta_resample(sum, t_array, 4, closed = CLOSED_LEFT, label = LABEL_RIGHT)
4-element TimeArray{Int64, Int64}:
 TimeTick(4, 3)
 TimeTick(8, 22)
 TimeTick(12, 38)
 TimeTick(16, 25)

julia> ta_resample(sum, t_array, 4, closed = CLOSED_RIGHT, label = LABEL_LEFT)
4-element TimeArray{Int64, Int64}:
 TimeTick(0, 7)
 TimeTick(4, 26)
 TimeTick(8, 42)
 TimeTick(12, 13)

julia> ta_resample(sum, t_array, 4, closed = CLOSED_RIGHT, label = LABEL_RIGHT)
4-element TimeArray{Int64, Int64}:
 TimeTick(4, 7)
 TimeTick(8, 26)
 TimeTick(12, 42)
 TimeTick(16, 13)
```

```jldoctest
julia> using Dates

julia> t_array = TimeArray{DateTime,Float64}([
           TimeTick(DateTime("2024-01-01"), 1.0),
           TimeTick(DateTime("2024-01-02"), 2.0),
           TimeTick(DateTime("2024-01-03"), 3.0),
           TimeTick(DateTime("2024-01-09"), 4.0),
           TimeTick(DateTime("2024-01-12"), 5.0),
           TimeTick(DateTime("2024-01-13"), 6.0),
           TimeTick(DateTime("2024-01-20"), 7.0),
       ]);

julia> ta_resample(x -> isempty(x) ? NaN : maximum(x), t_array, Day(3))
7-element TimeArray{DateTime, Float64}:
 TimeTick(2024-01-01T00:00:00, 3.0)
 TimeTick(2024-01-04T00:00:00, NaN)
 TimeTick(2024-01-07T00:00:00, 4.0)
 TimeTick(2024-01-10T00:00:00, 5.0)
 TimeTick(2024-01-13T00:00:00, 6.0)
 TimeTick(2024-01-16T00:00:00, NaN)
 TimeTick(2024-01-19T00:00:00, 7.0)
```
