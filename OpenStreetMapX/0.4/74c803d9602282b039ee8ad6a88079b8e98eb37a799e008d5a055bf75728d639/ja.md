```
classify_cycleways(ways::Vector{OpenStreetMapX.Way},
                   classes::Dict{String, Int} = OpenStreetMapX.CYCLE_CLASSES)
```

OpenStreetMapXのウェイのベクトルをそのサイクルウェイ属性に基づいて分類します。"bicycle"、"cycleway"、および"highway"タグの存在を考慮し、対応する値または構築されたクラス文字列が指定されたクラス辞書に存在するかどうかをチェックします。

**引数**

  * `ways::Vector{OpenStreetMapX.Way}` : ウェイのベクトル
  * `classes` : クラス辞書
