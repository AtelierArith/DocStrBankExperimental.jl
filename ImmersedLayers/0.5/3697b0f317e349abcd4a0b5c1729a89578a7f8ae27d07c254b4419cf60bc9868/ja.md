```
AreaForcingModel(model_function!)
```

全領域にわたる面タイプの強制を作成し、`model_function!`（強制の強さを返す関数）を使用します。

`model_function!` は、次の形式の署名を持つインプレースでなければなりません。

```
  model_function!(str,state,t,fcache,phys_params)
```

ここで、`str` は返される強さ、`state` は状態ベクトル、`t` は時間、`fcache` は対応する `AreaRegionCache`、`phys_params` はユーザーが提供する物理パラメータです。これらのいずれかを利用して強さを計算できます。

キーワード `spatialfield =` は、強さを評価するのに役立つ `AbstractSpatialField` を提供できます。（生成されたフィールドは、`fcache` の `generated_field` フィールド内で `model_function!` に利用可能です。）
