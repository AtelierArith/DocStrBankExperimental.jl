```
BinnedWeightedResampling(left_bin_edges, weights, n::Int; bin_repr = UncertainScalarKDE)
BinnedWeightedResampling(UncertainScalarKDE, left_bin_edges, weights, n::Int)
BinnedWeightedResampling(UncertainScalarPopulation, left_bin_edges, weights, n::Int)
BinnedWeightedResampling(RawValues, left_bin_edges, weights, n::Int)
```

これは、ビンごとの再サンプリングを実行することを示していますが、データセット内の各ポイントに異なる重みを付けます。

## フィールド

  * `left_bin_edges`。ビンの左端点。範囲または `minimum` と `step` メソッドを実装するカスタムタイプのいずれか。
  * `weights`。各ポイントに割り当てられた相対的な確率重み。
  * `n`。合計の引き出し数。これらは `weights` に従ってデータセットのポイントに分配されます。
  * `bin_repr`。各ビンをどのように要約するかを示す不確実な値のタイプ（各ビンのカーネル密度推定分布のための `UncertainScalarKDE`、各ビンの値を等確率の集団として表すための `UncertainScalarPopulation`）または要約せずに各ビンに落ちる生の値を返す（`RawValues`）。

## 例

```julia
using UncertainData, StatsBase

# 0から200まで20刻みのグリッドで再サンプリング
grid = 0:20:200

# データセットに50ポイントがあると仮定します。ランダムな重みを割り当てます。
wts = Weights(rand(50))

# 合計の引き出し数（平均して1000000/50 = 20000引き出し/ポイント
# 重みが等しい場合）
n_draws = 10000000

# 再サンプリングスキームを作成します。各ビンの分布にカーネル密度推定を使用します。
resampling = BinnedWeightedResampling(grid, wts, n_draws, bin_repr = UncertainScalarKDE)

# 各ビンを等確率の集団として表現します
resampling = BinnedWeightedResampling(grid, wts, n_draws, bin_repr = UncertainScalarPopulation)

# 各ビンの生の値を保持します（本質的には UncertainScalarPopulation と同じですが、
# 集団メンバーのための追加の重みベクトルを保存することを避けます）。
resampling = BinnedWeightedResampling(grid, wts n_draws, bin_repr = RawValues)
```
