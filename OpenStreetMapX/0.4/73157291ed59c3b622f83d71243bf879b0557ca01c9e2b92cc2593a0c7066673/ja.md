```
classify_walkways(ways::Vector{OpenStreetMapX.Way},
                  classes::Dict{String, Int} = OpenStreetMapX.PED_CLASSES)
```

OpenStreetMapXのウェイのベクトルをその歩行者属性に基づいて分類します。"sidewalk"タグの存在を考慮し、対応する値または"highway"タグの値が指定されたクラス辞書に存在するかどうかをチェックします。

**引数**

  * `ways::Vector{OpenStreetMapX.Way}` : ウェイのベクトル
  * `classes` : クラス辞書
