```
  AreaForcingModel(shape::Union{Body,BodyList},transform::MotionTransform,model_function!)
```

形状（すなわち、`Body`、`BodyList`）と、形状を配置する場所を指定するための`transform`、および強制力の強さを返す関数`model_function!`をバンドルします。`model_function!`は、次の形式の署名を持つインプレース関数でなければなりません。

```
  model_function!(str,state,t,fcache,phys_params)
```

ここで、`str`は返される強さ、`state`は状態ベクトル、`t`は時間、`fcache`は対応する`AreaRegionCache`、`phys_params`はユーザーが提供する物理パラメータです。これらのいずれかを使用して強さを計算できます。

渡すことができるキーワード引数がいくつかあります：`ddftype =`はDDFのタイプを指定し、`spatialfield =`は強さを評価するのに役立つ`AbstractSpatialField`を提供します。（生成されたフィールドは、`fcache`の`generated_field`フィールド内で`model_function!`に利用可能です。）
