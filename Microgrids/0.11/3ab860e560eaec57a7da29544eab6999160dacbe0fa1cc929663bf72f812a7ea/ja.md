```
simulate(mg::Microgrid, smoothing::Smoothing=NoSmoothing)
```

マイクログリッド `mg` の技術的および経済的パフォーマンスをシミュレートします。

不連続な計算は、オプションで `Smoothing` パラメータ `transition` と `gain` を使用して平滑化（緩和）できます（そのドキュメントを参照）。勾配ベースの最適化を使用する場合は、平滑化を推奨します。

返されるもの：

  * `sim_operation` からの運用軌道（将来のバージョンではオプションであるべき）
  * `sim_operation` からの運用統計
  * `sim_economics` からのマイクログリッドプロジェクトコスト
