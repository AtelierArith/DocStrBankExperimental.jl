```
abstract type AbstractCorrespondence
```

ブロブと測定値の間の対応関係を決定するためのメソッド。

関数 `assign(c::AbstractCorrespondence, blobs, coordinates)`、`too_far(c::AbstractCorrespondence, blob, coordinate)` をサポートします。

# サブタイプ

  * `HungarianCorrespondence`
  * `NearestNeighborCorrespondence`
