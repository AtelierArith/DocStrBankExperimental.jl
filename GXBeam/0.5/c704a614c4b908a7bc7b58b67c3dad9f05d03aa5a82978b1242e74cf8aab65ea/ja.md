```
set_internal_forces!([x,] system::Union{StaticSystem,DynamicSystem}, Fi, ielem)
```

要素 `ielem` の内部力に対応する `system`（またはベクトル `x`）の状態変数を、提供された値に設定します。
