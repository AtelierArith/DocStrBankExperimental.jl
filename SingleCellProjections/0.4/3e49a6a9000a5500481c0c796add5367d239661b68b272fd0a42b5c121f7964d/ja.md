```
covariate(src, type=:auto)
```

`src`を参照する`covariate`を作成します。

`src`は次のいずれかです：

  * `String` - DataMatrix `obs`の列を参照します。
  * `DataFrame` - 正確に2つの列を持ち、最初の列には`obs`のIDと一致するIDが含まれ、2番目の列には共変量が含まれます。
  * `Annotations`（実験的） - DataMatrix `obs`と一致するIDを持ち、共変量のための2番目の列があります。

`type`は`:auto`、`:numerical`、`:categorical`、`:twogroup`、`:intercept`のいずれかでなければなりません。`:auto`は、列の値が数値かカテゴリかを確認することによる自動検出を意味します。`type==:intercept`はモデルに切片を追加します（この場合、`src`パラメータは無視されます）。

参照： [`designmatrix`](@ref)
