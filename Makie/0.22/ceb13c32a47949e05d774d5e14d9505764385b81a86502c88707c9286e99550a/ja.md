```
origin!([mode = Absolute], t::Transformable, xyz...)
origin!([mode = Absolute], t::Transformable, xyz::VecTypes)
```

変換可能な `t` の原点を指定された `xyz` 値に設定します。これは `rotate!(t, ...)` および `scale!(t, ...)` の原点に影響します。`mode` が `Accum` として指定された場合、原点は指定された `xyz` によって移動されます。
