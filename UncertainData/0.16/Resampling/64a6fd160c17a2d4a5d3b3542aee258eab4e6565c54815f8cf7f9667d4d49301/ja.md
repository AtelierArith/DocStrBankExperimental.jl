```
InterpolateAndBin{L}(f::Function, left_bin_edges, intp::L, intp_grid,
    extrapolation_bc::Union{<:Real, Interpolations.BoundaryCondition})
```

は、インデックスと値の両方からなるデータセットを、提供された `intp` スキーム（例：`Linear()`）を使用して `intp_grid` グリッドに最初に補間する必要があることを示しています。補間後、`left_bin_edges` で定義されたビンに補間された値を割り当て、各ビンに入る値を要約関数 `f`（例：`mean`）を使用して要約します。

## 例

```julia
using UncertainData, Interpolations, StatsBase

# NaN 値を含む以下の不均等に間隔を空けたデータがあると仮定します
T = 100
time = sample(1.0:T*5, T, ordered = true, replace = false)
y1 = rand(T)
time[rand(1:T, 10)] .= NaN 
y1[rand(1:T, 10)] .= NaN 

# 最初にデータセットを `0.1` 時間単位の規則的な時間グリッドに線形補間したいと考えています。
intp = Linear()
intp_grid = 0:0.1:1000
extrapolation_bc = Flat(OnGrid())

# 次に、時間ビン `50` 時間単位の幅でデータセットをビンに分け、各ビンのすべての値を収集し、`f` を使用して要約します。
f = mean
left_bin_edges = 0:50:1000

r = InterpolateAndBin(f, left_bin_edges, intp, intp_grid, extrapolation_bc)
```
