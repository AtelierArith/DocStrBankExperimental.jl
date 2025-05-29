```
mean(loss, outputs, targets, weights; normalize=true)
```

`loss` の値の平均を `outputs` と `targets` のイテラブルに対して返します。`weights` は各観測値の重要性を決定します。オプション `normalize` は結果を重みの合計で割ります。
