```
CoverTree(ϵ::Real, lloyds::Bool=true, voronoi::Bool=true, metric::SemiMetric=Euclidean())
```

CoverTreeアルゴリズム[1]は、与えられたデータセットを`metric`距離に従って最適にカバーするツリーを再帰的に構築します。

## 引数:

  * `ϵ::Real`: 空間解像度。高い`ϵ`はポイント数を減少させます。
  * `lloyds::Bool`: 他の誘導点が近くにない場合、サンプリングされたデータポイントの代わりにその周りに作成されたボールの重心を使用します。
  * `voronoi::Bool`: 各層の処理の最後に各ノードにサンプルを再割り当てします。
  * `metric::SemiMetric`: ポイント間の距離を決定するために使用される距離メトリックです。

[1] Alexander Terenin, David R. Burt, Artem Artemev, Seth Flaxman, Mark van der Wilk, Carl Edward Rasmussen, Hong Ge: 数値的に安定したスパースガウス過程をカバー木を使用して最小分離で実現する: https://arxiv.org/abs/2210.07893
