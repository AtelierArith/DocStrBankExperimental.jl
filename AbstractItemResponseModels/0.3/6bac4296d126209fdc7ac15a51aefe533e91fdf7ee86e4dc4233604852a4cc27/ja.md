```
ItemResponseModel
```

アイテム応答理論モデルを表す抽象型です。

各実装 `T <: ItemResponseModel` は、以下の特性を定義しなければなりません：

  * [`response_type`](@ref): 有効な [`ResponseType`](@ref)
  * [`person_dimensionality`](@ref): 人のパラメータの次元数
  * [`item_dimensionality`](@ref): アイテムのパラメータの次元数
  * [`estimation_type`](@ref): 有効な [`EstimationType`](@ref)

さらに `T <: ItemResponseModel` は、以下のインターフェースを実装しなければなりません：

  * [`irf`](@ref): 特定の応答でアイテムに回答する能力推定を持つ人の確率を返すアイテム応答関数。
  * [`iif`](@ref): 能力推定に基づいて特定の応答でアイテムに回答する情報を返すアイテム情報関数。
  * [`expected_score`](@ref): 能力推定に基づいて1つまたは複数のアイテムの期待スコアを返す期待スコア関数。
  * [`information`](@ref): 能力推定に基づいて1つまたは複数のアイテムの情報を返す情報関数。
  * [`fit`](@ref): 観測データに対してタイプ `T` のアイテム応答モデルをフィッティングする関数。
  * [`get_item_locations`](@ref): 特定のアイテムのアイテム位置を返す関数。
  * [`get_person_locations`](@ref): 特定の人の人位置を返す関数。
