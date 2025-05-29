```
PointForcingModel(point_function::Function,transform::MotionTransform,model_function!::Function)
```

強制点の位置を返す関数である `point_function`、点の座標系の原点が慣性系の原点に対してどこにあるかを指定するための `transform`、および強制の強さを返す関数である `model_function` をバンドルします。

`point_function` は次の形式のアウトオブプレースシグネチャを持つ必要があります。

```
  point_function(state,t,fcache,phys_params)
```

ここで `state` は状態ベクトル、`t` は時間、`fcache` は対応する `PointRegionCache` であり、`phys_params` はユーザーが提供する物理パラメータです。これらのいずれかを利用して位置を計算することができます。各座標のベクトルまたは `VectorData` を返す必要があります。

`model_function!` は次の形式のインプレースシグネチャを持つ必要があります。

```
  model_function!(str,state,t,fcache,phys_params)
```

ここで `str` は返される強さです。
