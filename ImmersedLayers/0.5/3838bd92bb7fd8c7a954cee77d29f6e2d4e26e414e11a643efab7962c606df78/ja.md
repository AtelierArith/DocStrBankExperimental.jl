```
  LineForcingModel(shape::Union{Body,BodyList},transform::MotionTransform,model_function!)
```

`shape`（すなわち、`Body`、`BodyList`）、`transform`（形状を配置する場所を指定するため）、および`model_function!`（強制の強さを返す関数）をバンドルします。`model_function!`は、次の形式の署名を持つインプレースでなければなりません。

```
  model_function!(str,state,t,fcache,phys_params)
```

ここで、`str`は返される強さ、`state`は状態ベクトル、`t`は時間、`fcache`は対応する`LineRegionCache`、`phys_params`はユーザーが提供する物理パラメータです。これらのいずれかを使用して強さを計算できます。

キーワード`ddftype =`を使用してDDFのタイプを指定できます。
