```
residual!(res, yd, y::MVector{S, SimFloat}, s::KPS3, time) where S

N点テザー模型、上部に1点のカイト:
入力:
状態ベクトル y   = pos1, pos2, ..., posn, vel1, vel2, ..., veln
導関数   yd  = vel1, vel2, ..., veln, acc1, acc2, ..., accn
出力:
残差     res = res1, res2 = pos1,  ..., vel1, ...

追加パラメータ:
s: 作業変数を持つ構造体、タイプ KPS3
S: 状態ベクトルの次元
```

モデルの点質量の数 N = S/6、各点の状態は2つの3要素ベクトルで表されます。
