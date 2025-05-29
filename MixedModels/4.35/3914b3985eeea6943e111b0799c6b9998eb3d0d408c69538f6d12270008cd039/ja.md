```
columntable(s::OptSummary, [stack::Bool=false])
```

`s.fitlog`を`Tables.columntable`として返します。

`stack`がfalse（デフォルト）の場合、結果には3つの列があります：

  * `iter`: イテレーション番号
  * `objective`: そのサンプルでの目的関数の値
  * `θ`: そのサンプルでのパラメータベクトル

`stack`がtrueの場合、4つの列があります：`iter`、`objective`、`par`、および`value`。ここで`value`は`θ`ベクトルのスタックされた内容（`vcat(θ...)`に相当）であり、`par`はパラメータ番号のベクトルです。
