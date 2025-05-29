```
EdgeTrackingResults(edge, track1, track2, time, bisect_idx)
```

[`edgetracking`](@ref)アルゴリズムの出力を格納するデータ型です。

## フィールド

  * `edge::StateSpaceSet`: トラックされたエッジセグメントを表す擬似軌道（`track1`と`track2`の間の状態空間の平均によって与えられます）
  * `track1::StateSpaceSet`: 流域1内のエッジを追跡する擬似軌道
  * `track2::StateSpaceSet`: 流域2内のエッジを追跡する擬似軌道
  * `time::Vector`: 上記の`StateSpaceSet`の時間点
  * `bisect_idx::Vector`: 再二分が発生した`time`のインデックス
  * `success::Bool`: エッジトラッキングが成功したかどうかを示します
