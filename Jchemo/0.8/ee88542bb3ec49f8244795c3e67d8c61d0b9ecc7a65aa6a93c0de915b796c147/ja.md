```
mblock(X, listbl)
```

行列からブロックを作成します。

  * `X` : Xデータ (n, p)。
  * `listbl` : 各要素が `X` のブロックを定義する列番号を定義するベクトル。 `listbl` の長さはブロックの数です。

この関数はブロックのリスト（ベクトル）を返します。

## 例

```julia
using Jchemo
n = 5 ; p = 10 
X = rand(n, p) 
listbl = [3:4, 1, [6; 8:10]]

Xbl = mblock(X, listbl)
Xbl[1]
Xbl[2]
Xbl[3]
```
