```
arrange!(X[,n::Integer])
arrange!(X[,P::Vector])
```

ktensorのランク1成分を整列します：因子行列の列を正規化し、ktensor成分を大きさ順にソートします（大きいものから小さいものへ）。ktensorを書き換えます。

## 引数:

  * `n`: 重みをλの代わりにn番目の因子行列に吸収します。
  * `P`: Xの成分を置換Pに従って再配置します。Pは1からncomponents(X)までの置換である必要があります。
