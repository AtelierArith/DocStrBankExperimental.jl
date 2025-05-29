```
MotionTransform(xA_to_B::SVector,RA_to_B::SMatrix) -> MotionTransform
```

運動ベクトルのプルッカー変換行列を計算し、システムAからシステムBに変換します。入力の `xA_to_B` は、Aの原点からBの原点までのユークリッドベクトルで、A座標系で表現されています。また、`RA_to_B` は、システムAの座標をシステムBの座標に変換する回転行列です。結果の行列は次の形になります。

$$
{}^B T^{(m)}_A = \begin{bmatrix} R & 0 \\ 0 & R \end{bmatrix} \begin{bmatrix} 1 & 0 \\ -x^\times & 1 \end{bmatrix}
$$

`xA_to_B` を標準ベクトルとして、`RA_to_B` を標準の3 x 3行列として提供することもできます。

`xA_to_B` の長さが3の場合、三次元変換（6 x 6プルッカー変換）が作成されます。`xA_to_B` の長さが2の場合、二次元変換（3 x 3プルッカー変換）が返されます。
