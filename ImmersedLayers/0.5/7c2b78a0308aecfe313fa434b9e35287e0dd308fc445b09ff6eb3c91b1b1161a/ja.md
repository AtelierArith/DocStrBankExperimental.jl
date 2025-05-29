```
  PointForcingModel(pts::VectorData,transform::MotionTransform,model_function!)
```

ポイント座標 `pts`、`transform`（点の座標系の原点が慣性系の原点に対してどこにあるかを指定するため）、およびポイントタイプの強制の強さを返す関数 `model_function!` を束ねます。 `model_function!` は、次の形式の署名を持つインプレース関数でなければなりません。

```
  model_function!(str,state,t,fcache,phys_params)
```

ここで `str` は返される強さ、`state` は状態ベクトル、`t` は時間、`fcache` は対応する `PointRegionCache`、`phys_params` はユーザーが提供する物理パラメータです。これらのいずれかを使用して強さを計算できます。

キーワード `ddftype =` を使用して DDF のタイプを指定できます。
