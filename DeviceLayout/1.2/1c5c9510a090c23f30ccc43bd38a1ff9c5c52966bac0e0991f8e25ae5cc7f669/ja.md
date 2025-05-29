```
layer_inclusion(only_layers, ignore_layers)
```

`f(m::Meta)`という関数を返し、包含/除外ルールに基づいて`Bool`を返します。

`only_layers`と`ignore_layers`は、`DeviceLayout.Meta`、レイヤー名`Symbol`、またはそれらのコレクションです。

`only_layers`が空である場合、`ignore_layers`のみが使用され、`f(m)`は`m`または`layer(m)`が`ignore_layers`に含まれていないことを確認します。それ以外の場合、`f(m)`は`m`または`layer(m)`が`only_layers`に含まれていることも確認します。
