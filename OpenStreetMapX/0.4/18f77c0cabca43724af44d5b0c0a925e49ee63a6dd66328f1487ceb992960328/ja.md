```
filter_cycleways(ways::Vector{OpenStreetMapX.Way},
                classes::Dict{String, Int} = OpenStreetMapX.CYCLE_CLASSES;
                levels::Set{Int} = Set(1:length(OpenStreetMapX.CYCLE_CLASSES)))
```

OpenStreetMapXのウェイのベクターをフィルタリングして、自転車道に関連するものだけを含めます。"bicycle"、"cycleway"、および "highway" タグの存在を考慮し、対応する値または構築されたクラス文字列が指定されたクラス辞書およびレベルセットに存在するかどうかを確認します。

**引数**

  * `ways::Vector{OpenStreetMapX.Way}` : ウェイのベクター
  * `classes` : クラス辞書
  * `levels` : ウェイタグと比較するのに役立つレベルのセット
