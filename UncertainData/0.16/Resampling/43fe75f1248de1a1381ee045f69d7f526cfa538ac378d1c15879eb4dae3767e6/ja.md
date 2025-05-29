```
BinnedMeanWeightedResampling
```

ビンごとの再サンプリングで、各ビンはそのビンに入るすべてのサンプルの平均を使用して要約されます。データセット内のポイントは、`weights`に従って確率的にサンプリングされます。

## フィールド

  * `left_bin_edges`。ビンの左端点。範囲または`minimum`および`step`メソッドを実装するカスタムタイプのいずれか。
  * `weights`。各ポイントに割り当てられた相対的な確率重み。
  * `n`。サンプルの総数。これらは`weights`に従ってデータセットのポイントに分配されます。

## 例

```julia
using UncertainData, StatsBase

# 0から200までのグリッドで20刻みで再サンプリング
grid = 0:20:200

# データセットに50ポイントがあると仮定します。それらにランダムな重みを割り当てます。
wts = Weights(rand(50))

# サンプルの総数（平均して1000000/50 = 20000サンプル/ポイント
# 重みが等しい場合）
n_draws = 10000000

# 再サンプリングスキームを作成
resampling = BinnedMeanWeightedResampling(grid, wts, n_draws)
```
