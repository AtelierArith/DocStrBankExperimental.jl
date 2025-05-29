```
ta_rolling(f::Function, t_array::TimeArray, n::Int; kw...) -> TimeArray
```

関数 `f` をウィンドウサイズ `n` のスライディングウィンドウで `t_array` の要素に適用します。関数 `f` は、型 `V` の要素を持つベクトルを入力として受け取り、新しい値を返す必要があります。この値は各ウィンドウの対応するタイムスタンプに割り当てられます。

## キーワード引数

  * `observations::Integer = n`: 値を計算するためのローリングウィンドウ内の観測数（そうでなければ `NaN`）。

関数シグネチャ：

```julia
f(x::AbstractVector{V})::Any = ...
```

## 例

```jldoctest
julia> using Dates

julia> t_array = TimeArray([
           TimeTick(DateTime("2024-01-01"), 1.0),
           TimeTick(DateTime("2024-01-03"), 2.0),
           TimeTick(DateTime("2024-01-04"), 3.0),
           TimeTick(DateTime("2024-01-07"), 4.0),
           TimeTick(DateTime("2024-01-09"), 5.0),
       ]);

julia> ta_rolling(sum, t_array, 3)
5-element TimeArray{DateTime, Float64}:
 TimeTick(2024-01-01T00:00:00, NaN)
 TimeTick(2024-01-03T00:00:00, NaN)
 TimeTick(2024-01-04T00:00:00, 6.0)
 TimeTick(2024-01-07T00:00:00, 9.0)
 TimeTick(2024-01-09T00:00:00, 12.0)

julia> ta_rolling(sum, t_array, 3; observations = 1)
5-element TimeArray{DateTime, Float64}:
 TimeTick(2024-01-01T00:00:00, 1.0)
 TimeTick(2024-01-03T00:00:00, 3.0)
 TimeTick(2024-01-04T00:00:00, 6.0)
 TimeTick(2024-01-07T00:00:00, 9.0)
 TimeTick(2024-01-09T00:00:00, 12.0)

```
