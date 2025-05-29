```
filter_walkways(ways::Vector{OpenStreetMapX.Way},
                classes::Dict{String, Int} = OpenStreetMapX.PED_CLASSES;
                levels::Set{Int} = Set(1:length(OpenStreetMapX.PED_CLASSES)))
```

歩行者用歩道に関連するものだけを含むように、ウェイのベクターをフィルタリングします。これは、「側道」タグの存在を考慮し、対応する値または「ハイウェイ」タグの値が指定されたクラス辞書およびレベルセットに存在するかどうかをチェックします。

**引数**

  * `ways::Vector{OpenStreetMapX.Way}` : ウェイのベクター
  * `classes` : クラス辞書
  * `levels` : ウェイタグと比較するのに役立つレベルのセット
