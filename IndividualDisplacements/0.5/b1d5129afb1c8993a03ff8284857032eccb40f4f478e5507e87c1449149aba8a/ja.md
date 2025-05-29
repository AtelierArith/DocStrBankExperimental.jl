```
postprocess_xy(sol,P::FlowFields,D::NamedTuple; id=missing, T=missing)
```

`sol`を`DataFrame`にコピーし、位置をx,y座標にマッピングし、単純な二重周期ドメインのための時間軸を定義します。
