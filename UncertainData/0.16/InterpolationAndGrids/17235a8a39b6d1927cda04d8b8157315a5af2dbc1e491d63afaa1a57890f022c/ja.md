```
bin(left_bin_edges::AbstractRange, xs, ys) -> Vector{Vector{T}} where T
```

`ys`の要素を、`left_bin_edges`で定義された`N`のグリッドポイントに基づいて、`N-1`の異なるビンベクターに分配します。もし`xs[i]`が`n`-番目のビン区間に入る場合、`ys[i]`は`n`-番目のビンベクターに割り当てられます。もし`xs[i]`がグリッドの外にある場合、対応する`ys[i]`は無視されます。詳細は[`bin!`](@ref)を参照してください。

`N - 1`のビンベクターを返します。

## 例

### 各ビンの値を取得する:

```julia
xs = [1.2, 1.7, 2.2, 3.3, 4.5, 4.6, 7.1]
ys = [4.2, 5.1, 6.5, 4.2, 3.2, 3.1, 2.5]
left_bin_edges = 0.0:1.0:6.0
bin(left_bin_edges, xs, ys)
```

```julia
# 不均等に間隔を空けた時間インデックスを持ついくつかの例データ
npts = 300
time, vals = sort(rand(1:1000, npts)), rand(npts)

# 時間インデックス100から900までの25時間ステップ幅の時間ビンに
# どの値が入るかを確認します。
left_bin_edges = 100:25:900

bin(left_bin_edges, time, vals)
```
