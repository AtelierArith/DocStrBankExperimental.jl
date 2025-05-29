```
layer_included(m::Meta, only_layers, ignore_layers)
```

`m` または `layer(m)` が包含/除外ルールに基づいて含まれているかどうかを返します。

`only_layers` と `ignore_layers` は、`DeviceLayout.Meta` のコレクションおよび/またはレイヤー名 `Symbol` のコレクションです。

`only_layers` が空である場合、`ignore_layers` のみが使用され、`layer_included` は `m` または `layer(m)` が `ignore_layers` に含まれていないことを確認します。それ以外の場合、`layer_included` は `m` または `layer(m)` が `only_layers` に含まれていることも確認します。
