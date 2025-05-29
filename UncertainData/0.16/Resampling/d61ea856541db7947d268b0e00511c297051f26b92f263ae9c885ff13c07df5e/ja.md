```
BinnedMeanResampling
```

ビンごとの再サンプリングで、各ビンはそのビンに入るすべての引き出しの平均を使用して要約されます。

## フィールド

  * `left_bin_edges`。ビンの左端点。範囲または `minimum` と `step` メソッドを実装するカスタムタイプのいずれか。
  * `n`。引き出しの数。データセット内の各点は `n` 回サンプリングされます。データセットに `m` 点がある場合、合計引き出し数は `n*m` です。

## 例

```julia
using UncertainData

# 0から200までを20刻みでグリッド上で再サンプリング
grid = 0:20:200

# データセット内の各点あたりのサンプル数
n_draws = 10000

# 再サンプリングスキームを作成
resampling = BinnedMeanResampling(grid, n_draws)
```
