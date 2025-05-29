```
assign_basic_individual_criteria!(data::Dict; chosen_criterion::String="rwlav")
```

データ["meas"]の測定に個別基準を割り当てる基本関数です。各測定について、少なくとも1つのフェーズの分布タイプが正規分布である場合、基準はchosen_criterionにデフォルト設定されます。それ以外の場合は、'mle'基準が割り当てられます。この関数は、単一の測定辞書（例：data["meas"]["1"]）または完全な数学的データモデルを入力として受け取ります。
