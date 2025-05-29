```julia
addDownVariableFactors!(dfg, subfg, cliq; ...)
addDownVariableFactors!(dfg, subfg, cliq, logger; solvable)

```

CSMでの下方解決に必要なクリークサブグラフにいくつかの変数と因子を追加する特別な関数です。

開発ノート

  * ツリーの上方解決と下方解決が正確に同じサブグラフを使用すべきかどうかにはまだいくつかの不一致があります... '上方用の間と下方用の前面接続'
