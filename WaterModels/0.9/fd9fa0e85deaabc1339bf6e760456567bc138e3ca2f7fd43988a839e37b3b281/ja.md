```
parse_epanet(path::String)
```

指定されたファイルパス `path` から [EPANET](https://www.epa.gov/water-research/epanet) (.inp) ファイルを解析し、WaterModels データ構造（データの辞書）を返します。EPANET フォーマットとその構成要素についての詳細な説明は、[OpenWaterAnalytics Wiki](http://wateranalytics.org/EPANET/_inp_file.html) を参照してください。また、この解析ルーチンは必ずしもトポロジーを保持せず、元の EPANET モデルとの一対一の対応を保証するものではありません。たとえば、バルブ（チェックまたはシャットオフ）を持つ各パイプは、WaterModels パイプコンポーネント *および* バルブコンポーネントに変換されます。データの修正やデータモデルの単位変換は行いません。
