```
Clock <: AbstractClock
Clock([t]; dt)
```

独立変数 `t` とティック間隔 `dt` を持つデフォルトの周期クロック。`dt` が指定されていない場合、可能であれば推測されます。
