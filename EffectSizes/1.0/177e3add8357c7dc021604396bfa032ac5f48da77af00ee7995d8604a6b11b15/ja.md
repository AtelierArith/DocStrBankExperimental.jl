```
BootstrapConfidenceInterval(lower, upper, quantile, bootstrap)
```

効果サイズの信頼区間の `lower` および `upper` 限界を指定された `quantile` で表す型で、`bootstrap` リサンプルを使用します。

```
BootstrapConfidenceInterval(f, xs, ys, bootstrap; quantile)
```

指定された `quantile` で `xs` と `ys` の2つのベクトル間のブートストラップ信頼区間を計算するために、`xs` と `ys` の `bootstrap` リサンプルに `f` を適用します。
