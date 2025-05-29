```julia
getCliqVarIdsPriors(cliq)
getCliqVarIdsPriors(cliq, allids)
getCliqVarIdsPriors(cliq, allids, partials)

```

この `cliq` に関連付けられた事前因子を持つ変数 id `::Int` を取得します。

注意:

  * 上向きまたは下向きのメッセージ伝達からのシングルトンメッセージは含まれません。
