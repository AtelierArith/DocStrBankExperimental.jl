```
(mxh::MXH)(n_points::Int=100; adaptive::Bool=true)
```

指定されたMXHの(r,z)ベクトルを返します。

`adaptive`がtrueの場合、`n_points`は単位円の周囲のために指定され、数は決して`n_points`未満にはなりません。
