```
  AreaForcingModel(shape::Union{Body,BodyList},transform::MotionTransform,model_function!)
```

`shape`（すなわち、`Body`、`BodyList`）、`transform`（形状を配置する場所を指定するため）、および面積タイプの強制のための`model_function!`（強制の強さを返す関数）を束ねます。`model_function!`は、次の形式の署名を持つインプレースでなければなりません。

```
  model_function!(str,state,t,fcache,phys_params)
```

ここで、`str`は返される強さ、`state`は状態ベクトル、`t`は時間、`fcache`は対応する`AreaRegionCache`、`phys_params`はユーザーが提供する物理パラメータです。これらのいずれかを利用して強さを計算できます。

渡すことができるキーワード引数がいくつかあります：`ddftype =`はDDFのタイプを指定し、`spatialfield =`は強さの評価を助けるために`AbstractSpatialField`を提供します。（結果として得られるフィールドは、`fcache`の`generated_field`フィールド内で`model_function!`に利用可能です。）
