```
graph(domain, localaniso, metric, searcher)
graph(domain, localaniso, metric, refvariogram, searcher)
```

graph(samples, domain, localaniso, metric, searcher)     graph(samples, domain, localaniso, metric, refvariogram, searcher)

`domain` と `samples` ポイントをローカルに接続するグラフを作成します。エッジ/隣接点の数は、ドメインに関連付けられた `searcher` オブジェクトによって定義されます。ポイント間の距離は、ローカル異方性 `localaniso` と、2つのポイント間の距離を計算するための望ましい `metric` に基づいています。利用可能なメトリック：

  * `AnisoDistance`   - 平均異方性距離
  * `KernelVariogram` - 非定常変動核推定器

メトリックが `KernelVariogram` の場合、参照変動 `refvariogram` が必要です。
