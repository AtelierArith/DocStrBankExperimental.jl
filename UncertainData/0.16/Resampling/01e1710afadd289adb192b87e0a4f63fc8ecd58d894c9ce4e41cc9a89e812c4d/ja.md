```
resample(udata::AbstractUncertainIndexValueDataset, regularization_scheme::InterpolateAndBin{Linear})
```

`udata`の単一の実現を描画し、提供された正則化スキームに従ってデータを補間およびビン分けします。`udata`のポイントは独立していると仮定し、補間する前にインデックス値に従って描画をソートします。詳細は[`InterpolateAndBin`](@ref)を参照してください。

## 例

```julia
npts = 50
y = rand(npts) 

N = Normal(0, 1)

for t in 3:npts
    y[t,1] = 0.7*y[t-1,1] - 0.35*y[t-2,1] + rand(N)
end

# データが不均等に間隔を空けていると仮定 
time = sample(1.0:npts*5, npts, ordered = true, replace = false)

# 時間インデックスと値の両方に不確実性を割り当て、 
# UncertainIndexValueDatasetに集める
utime = UncertainValue.(Normal.(time, 2))
uy = UncertainValue.(Normal.(y, 0.1))
udata = UncertainIndexValueDataset(utime, uy)

# 補間およびビン分けスキーム。まず非常に細かいグリッドに補間し、
# 次に各粗いビンに落ちるポイントを集め、各ビン内のポイントの平均を使用して 
# 各ビンを要約します。
left_bin_edges = 0:10:npts*5
r = InterpolateAndBin(mean, left_bin_edges, Linear(), 0:0.1:1000, Flat(OnGrid()))

# ビン分けされた時間軸:
time_binned = left_bin_edges[1:end-1] .+ step(left_bin_edges)/2

# 補間された（ビン分けされた）値に対応するセットを取得
y_binned = resample(udata, r)

# 補間された+ビン分けされた描画をプロット
time_binned = left_bin_edges[1:end-1] .+ step(left_bin_edges)/2

p = plot(xlabel = "time", ylabel = "value")
for i = 1:100
    plot!(time_binned, resample(udata, r), lw = 0.3, α = 0.2, ms = 0.1, c = :red, 
        marker = stroke(0.1), label = "")
end
plot!(time, y, c = :black, lw = 1, ms = 2, marker = stroke(2.0, :black), label = "")
plot!(udata, c = :black, lw = 1, ms = 2, marker = stroke(0.1, :black), [0.05, 0.95], [0.05, 0.95])
vline!(left_bin_edges, c = :black, α = 0.3, lw = 0.3, label = "")
```
