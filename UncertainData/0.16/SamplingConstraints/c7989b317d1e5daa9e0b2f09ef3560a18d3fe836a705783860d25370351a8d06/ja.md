```
sequence_exists(x, c::SequentialSamplingConstraint)
```

不確実なデータセット `x` を通るポイントごとのシーケンスが、基準 `c` を満たすかどうかを確認します。

`x` が `UncertainIndexValueDataset` の場合、インデックスのみを通るシーケンスをチェックします。

チェックが行われる前に、`x` の分布は `c` によって提供された分位点に切り詰められ、有限のサポートを持つことが保証されます。

## 例

```julia
# 時間インデックスのセットを作成 
# 増加するシーケンスが存在することを*知っている*方法でこれを構築します。 
t = [UncertainValue(Normal, i, 2) for i in 1:N];
sequence_exists(t, StrictlyIncreasing(StartToEnd()))
```
