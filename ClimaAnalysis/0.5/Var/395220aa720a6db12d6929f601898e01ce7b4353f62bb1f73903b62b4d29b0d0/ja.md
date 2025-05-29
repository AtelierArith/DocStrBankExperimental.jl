```
(x::OutputVar)(target_coord)
```

与えられた `target_coord` 座標に対して変数 `x` を多重線形補間を使用して補間します。

外挿は許可されておらず、ほとんどの場合 `BoundsError` が発生します。

次元の配列のいずれかの要素が `Dates.DateTime` の場合、補間は不可能です。Interpolations.jl は日付の補間をサポートしていません。経度が全範囲をカバーし、等間隔である場合、経度次元に周期境界条件が追加されます。緯度が全範囲をカバーし、等間隔である場合、緯度次元に平坦境界条件が追加されます。それ以外の場合、次元の配列の外で外挿するとエラーが発生します。

# 例

```jldoctest
julia> import ClimaAnalysis;

julia> time = 100.0:110.0 |> collect;

julia> z = 0.0:20.0 |> collect;

julia> data = reshape(1.0:(11 * 21), (11, 21));

julia> var2d = ClimaAnalysis.OutputVar(Dict("time" => time, "z" => z), data); var2d.([[105., 10.], [105.5, 10.5]])
2-element Vector{Float64}:
 116.0
 122.0
```
