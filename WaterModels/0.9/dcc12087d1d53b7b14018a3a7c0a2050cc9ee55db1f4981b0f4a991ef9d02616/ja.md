```
parse_file(
    path::String;
    skip_correct::Bool=false,
    per_unit::Bool=true
)
```

指定されたファイルパス `path` から [EPANET](https://www.epa.gov/water-research/epanet) (.inp) または JavaScript Object Notation (JSON) ファイルを解析し、データの辞書である WaterModels データ構造を返します。ここで、`skip_correct` が `true` に設定されている場合、データ修正ルーチン（例：コンポーネントの状態伝播）をスキップし、`per_unit` が `true` に設定されている場合、データモデルを単位あたりの測定システムに変換します。
