```
BinnedResampling(left_bin_edges, n::Int; bin_repr = UncertainScalarKDE)
BinnedResampling(UncertainScalarKDE, left_bin_edges, n::Int)
BinnedResampling(UncertainScalarPopulation, left_bin_edges, n::Int)
BinnedResampling(RawValues, left_bin_edges, n::Int)
```

ビン再サンプリングを実行する必要があることを示します。

## フィールド

  * `left_bin_edges`。ビンの左端点。範囲または `minimum` と `step` メソッドを実装するカスタム型のいずれか。
  * `n`。サンプル数。データセット内の各点は `n` 回サンプリングされます。データセット内に `m` 点がある場合、合計サンプル数は `n*m` です。
  * `bin_repr`。各ビンをどのように要約するかを示す不確実な値の型（各ビンのカーネル密度推定分布のための `UncertainScalarKDE`、各ビンの値を等確率の母集団として表すための `UncertainScalarPopulation`）または要約せずに各ビンに該当する生の値を返す（`RawValues`）。

## 例

```julia
using UncertainData

# 0から200まで20刻みのグリッドで再サンプリング
grid = 0:20:200

# データセット内の各点のサンプル数
n_draws = 10000

# 再サンプリングスキームを作成します。各ビンの分布にカーネル密度推定を使用します。
resampling = BinnedResampling(grid, n_draws, bin_repr = UncertainScalarKDE)

# 各ビンを等確率の母集団として表現します
resampling = BinnedResampling(grid, n_draws, bin_repr = UncertainScalarPopulation)

# 各ビンの生の値を保持します（本質的には UncertainScalarPopulation と同じですが、母集団メンバーの重みの追加ベクトルを保存するのを避けます）。
resampling = BinnedResampling(grid, n_draws, bin_repr = RawValues)
```
