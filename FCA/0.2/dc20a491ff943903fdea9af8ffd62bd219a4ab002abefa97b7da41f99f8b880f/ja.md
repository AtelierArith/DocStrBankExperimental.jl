```
mat_center(X; mat = "her")
```

この関数は入力をセンタリングします。もしXがエルミート行列であれば、$Xcen = X - Tr(X)/N*I$です。もしXが長方形行列であれば、$Xcen = X - X*ones(M,1)*ones(1,M)/M$です。

# 引数

  * `X`: エルミート行列または長方形行列
  * `mat`: `X`のタイプ、"her"と"rec"が有効なオプションです

# 出力:

  * `Xc`: `X`のセンタリングされたバージョン
