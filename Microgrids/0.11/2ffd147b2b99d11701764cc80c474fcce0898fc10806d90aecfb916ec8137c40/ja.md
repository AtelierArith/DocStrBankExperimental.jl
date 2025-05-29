```
aggregation(mg::Microgrid, oper_traj::OperationTraj, smoothing::Smoothing=NoSmoothing)
```

マイクログリッド `mg` のために、操作トラジェクトリ `oper_traj` を年間統計に集約します（`OperationStats` オブジェクトとして返されます）。

不連続な計算は、オプションで `Smoothing` パラメータ `transition` と `gain` を使用して平滑化（緩和）できます（それらのドキュメントを参照してください）。勾配ベースの最適化を使用する際には、平滑化が推奨されます。
