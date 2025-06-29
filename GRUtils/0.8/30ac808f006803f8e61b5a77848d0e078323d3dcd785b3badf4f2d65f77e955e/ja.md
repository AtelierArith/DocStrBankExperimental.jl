```
heatmap([x, y,] data; kwargs...)
```

ヒートマップを描画します。

現在のカラーマップは、二次元配列 `data` をヒートマップとして表示するために使用されます。

`data` が *N*×*M* 配列である場合、ヒートマップのセルは、座標 `x`（`M+1` の値を持つソートされたベクトル）と `y`（`N+1` の値を持つソートされたベクトル）によって定義される長方形のセルのグリッドにプロットされます。

`x` と `y` が指定されていない場合、X軸の区間 `[1, M+1]` と Y軸の区間 `[1, N+1]` を跨ぐ均一なグリッドが描画されます。

配列は左下隅に最初の値が描画されるため、場合によっては軸を反転させる必要があります。

デフォルトでは、列と行のインデックスがそれぞれ x 軸と y 軸に使用されるため、軸の制限を設定することをお勧めします。また、配列の値は現在の z 軸の制限内に収まる必要があるため、これらの制限を調整するか、配列の値の範囲をクリップする必要があるかもしれません。

# 例

```julia
# 左側の均一ヒートマップ
subplot(1,2,1)
x = LinRange(-2, 2, 40)
y = LinRange(0, pi, 20)
z = sin.(x') .+ cos.(y)
heatmap(z)
# 右側の非均一ヒートマップ
subplot(1,2,2)
x = [0, 2, 3, 4.5, 5]
y = [2, 3, 4.5, 5, 6, 8]
z = rand(5, 4)
heatmap(x, y, z)

```
