```
organise_obs(f, data; obsdim=_default_obsdim(data))
organise_obs(::ObsArrangement, data; obsdim=_default_obsdim(data))
```

`f`が期待する`ObsArrangement`に従って`data`を整理します。

# 引数

  * `f`: 特定の向きでデータを必要とする関数またはメソッド
  * `data`: 変換するデータ
  * `obsdim`: 観測の次元。指定されていない場合は`_default_obsdim`に戻ります。
