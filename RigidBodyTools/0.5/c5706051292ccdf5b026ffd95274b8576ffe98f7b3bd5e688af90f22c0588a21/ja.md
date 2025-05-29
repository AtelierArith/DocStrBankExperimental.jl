```
ForceTransform(xA_to_B::SVector,RA_to_B::SMatrix) -> ForceTransform
```

力ベクトルのための6 x 6プルッカー変換行列を計算し、システムAからシステムBに変換します。入力`xA_to_B`は、A座標系で表現されたAの原点からBの原点までのユークリッドベクトルであり、`RA_to_B`はシステムAの座標をシステムBの座標に変換する回転行列です。結果の行列は次の形になります。

$$
{}^B T^{(f)}_A = \begin{bmatrix} R & 0 \\ 0 & R \end{bmatrix} \begin{bmatrix} 1 & -x^\times \\ 0 & 1 \end{bmatrix}
$$
