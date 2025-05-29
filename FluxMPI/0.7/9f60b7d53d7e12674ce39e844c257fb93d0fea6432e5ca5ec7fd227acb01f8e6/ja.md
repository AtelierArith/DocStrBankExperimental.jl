```
DistributedOptimizer(optimizer)
```

`optimizer`を`DistributedOptimizer`でラップします。パラメータを更新する前に、非ブロッキングのAllreduceを使用してプロセス間で勾配を加算します。

## 引数

  * `optimizer`: Optimisers.jlパッケージと互換性のあるオプティマイザ

!!! 注     勾配が正しく平均化されるように、損失関数を`1 / total_workers()`でスケーリングすることを忘れないでください。
