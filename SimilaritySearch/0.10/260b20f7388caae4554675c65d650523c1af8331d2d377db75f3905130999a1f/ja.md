```
search(bs::BeamSearch, index::SearchGraph, q, res, hints, pools; bsize=bs.bsize, Δ=bs.Δ, maxvisits=bs.maxvisits)
```

`res`に指定された最近傍の集合に`q`を到達させようとします。

  * `bs`: `BeamSearch`のパラメータ
  * `index`: ローカル検索インデックス
  * `q`: クエリ
  * `res`: 結果オブジェクトで、結果を格納し、クエリの種類も指定します
  * `hints`: 検索のための出発点で、空のコレクションの場合はランダムに選択されます
  * `pools`: 事前に割り当てられたプールを持つ`SearchGraphPools`オブジェクト

オプションの引数（デフォルトは`bs`の値）

  * `bsize`: ビームサイズ
  * `Δ`: 探索拡張係数
  * `maxvisits`: 訪問するノードの最大数（距離評価）
