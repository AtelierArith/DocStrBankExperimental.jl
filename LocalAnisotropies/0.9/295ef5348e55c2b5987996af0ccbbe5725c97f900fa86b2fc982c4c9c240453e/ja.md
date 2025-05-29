```
deformspace(domain, localaniso, metric; kwargs)
deformspace(domain, localaniso, metric, refvariogram; kwargs)
```

deformspace(samples, domain, localaniso, metric; kwargs)     deformspace(samples, domain, localaniso, metric, refvariogram; kwargs)     deformspace(graphobject, metric=GraphDistance; kwargs)   kwargs = (anchors=1500, maxoutdim=200, weights=nothing)

空間変形は、座標を高次元の等方的空間に変換する方法であり、局所的な異方性情報が新しい距離に埋め込まれます。この新しいデータ構成では、従来の推定やシミュレーションを行うことができます。`domain`オブジェクト（適用される場合は`samples`）を指定する必要があります。局所的な異方性は`localaniso`を介して渡され、`metric`は局所的な異方性が新しいデータ距離を計算するためにどのように使用されるかを定義します。2点間の距離を計算するために利用可能なメトリックは次のとおりです：

  * `AnisoDistance`   - 平均異方性距離
  * `KernelVariogram` - 非定常変動核推定器
  * `GraphDistance`   - 情報を持つグラフの測地距離。グラフ構築の詳細は[`graph`](@ref)のドキュメントにあります。

メトリックが`KernelVariogram`の場合、参照変動`refvariogram`が必要です。追加のキーワード引数は、データ数が従来のMDSに対して大きすぎる場合にランドマークMDSを実行するための`anchors`の数です。`maxoutdim`は、MDS後に保持する最大次元数です。`weights`は、変換のためにデクラスタリングされたアンカーポイントを選択するのを助けるためのドメインデータ（+サンプル）のデクラスタリング重みです。
