```
reordermesh(fens, fes, ordering)
```

メッシュを再順序付けします（ノードを再シャッフルし、接続をそれに応じて再番号付けします）。

# 引数

  * `fens`: メッシュノードのセット。
  * `fes`: 要素のセット。
  * `ordering`: ノードと要素の希望する順序。

# 戻り値

再順序付けされたメッシュノードと要素。

順序はReverse Cuthill-McKey（パッケージSymRCM）から来る場合があります。
