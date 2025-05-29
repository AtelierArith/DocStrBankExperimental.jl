```
I = classify(cube::GItype, model; class_names::Union{String, Vector{String}}="") -> GMTimage
```

  * `cube`: 分類するためのバンドデータを持つキューブ。
  * `model`: `train_raster` 関数から得られた訓練済みモデル。
  * `class_names`: カテゴリカルカラーバーで使用するクラス名の文字列ベクター、またはそれらのクラス名をカンマ区切りで単一の文字列として指定します。クラス名の数は、`train_raster` でモデルを訓練したときに使用した数と一致する必要があります。
