```
get_lipschitz(model)
```

リプシッツ境界をリプシッツ境界を持つモデルから抽出します

リプシッツ境界を浮動小数点数として返します。この関数は以下のタイプでのみ機能します：

  * `LBDN` および `DiffLBDN`
  * `DenseLBDNParams` および `DirectLBDNParams`
  * `LipschitzRENParams`
