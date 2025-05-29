```
intermittent_correlation(
    data::AbstractVector; 
    maxdelta = length(data) ÷ 10, 
    types::Function = x -> true,
    show_progress::Bool = true,
)
```

時系列の間欠相関関数を計算します。つまり、ステップ `i` に値が存在した場合、時系列のステップ `i + delta` で同じタイプの値を見つける確率を計算します。

`0:maxdelta` のインデックスを持つ `OffsetArray` を返します。位置 `0` の値は `1.0` で、イベントの正規化カウントに対応します。

# 引数

  * `data::AbstractVector`: 分析する時系列。
  * `maxdelta::Integer`: 考慮する最大デルタステップ。デフォルトは `length(data) ÷ 10`。
  * `types` (オプション): 考慮すべきデータのタイプに対して `true` を返す関数。デフォルトはすべてのデータ、すなわち `x -> true`。例えば、`0` の値を無視するには、`types = x -> x != 0` を使用します。
  * `show_progress::Bool`: 進行状況バーを表示します。デフォルトは `true`。

# 例

ここでは、1 と 0 のシーケンス（`[1, 0, 1, 0, ...]`）からなる 10,000 要素の時系列を生成し、間欠相関関数を計算します。奇数ステップの後に同じ数（0 または 1）を見つける確率は 0 であり、偶数ステップの後に同じ数を見つける確率は 1 です。

```jldoctest
julia> using MolSimToolkit

julia> data = [ mod(i,2) for i in 1:10^4 ];

julia> intermittent_correlation(data; maxdelta=4, show_progress=false)
5-element OffsetArray(::Vector{Float64}, 0:4) with eltype Float64 with indices 0:4:
 1.0
 0.0
 1.0
 0.0
 1.0

julia> intermittent_correlation(data; maxdelta=4, types = x -> x != 0, show_progress=false)
5-element OffsetArray(::Vector{Float64}, 0:4) with eltype Float64 with indices 0:4:
 1.0
 0.0
 1.0
 0.0
 1.0
```

2 回目の実行では、`0` の値を無視しており、結果は同じです。なぜなら、ここでの `1` の値の相関は `0` の値の相関と同じだからです。

!!! compat
    この関数は MolSimToolkit のバージョン 1.9.0 で追加されました。`types` 引数はバージョン 1.10.0 で追加され、`show_progress` 引数はバージョン 1.28.0 で追加されました。


```
