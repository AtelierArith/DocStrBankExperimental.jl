```
setup_table!(config, data, ::Val{:branch})
```

ブランチテーブルを設定します。

  * `f_bus_idx` と `t_bus_idx` を反転させて、`f_bus_idx` < `t_bus_idx` になるようにします。
  * bus[:connected*branch*idxs] を作成し、そのバスを出る各ブランチの符号付きインデックスのベクターを含みます。(`+` は `f_bus_idx`、`-` は `to_bus_idx` です)。
