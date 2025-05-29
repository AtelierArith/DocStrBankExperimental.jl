```
fconcat()
```

水平方向にマルチブロックXデータを連結します。

  * `Xbl` : Xデータのブロックのリスト（行列のベクトル）    通常、(n, p)データからの関数`mblock`の出力です。

## 例

```julia
using Jchemo
n = 5 ; m = 3 ; p = 9 
X = rand(n, p) 
Xnew = rand(m, p)
listbl = [3:4, 1, [6; 8:9]]
Xbl = mblock(X, listbl) 
Xblnew = mblock(Xnew, listbl) 
@head Xbl[3]

fconcat(Xbl)
```
