```
residual!(res, yd, y::MVector{S, SimFloat}, s::KPS4, time) where S

N点テザー模型、上部の凧のための4つの点：
入力：
状態ベクトル y   = pos1,  pos2, ... , posn,  vel1,  vel2, . .., veln,  length, v_reel_out
導関数   yd  = posd1, posd2, ..., posdn, veld1, veld2, ..., veldn, lengthd, v_reel_outd
出力：
残差     res = res1, res2 = vel1-posd1,  ..., veld1-acc1, ..., 

追加パラメータ：
s: 作業変数を持つ構造体、型 KPS4
S: 状態ベクトルの次元
```

モデルの点質量の数 N = S/6、各点の状態は2つの3要素ベクトルで表されます。
