```
eulerRotationMat(α::FT, β::FT, γ::FT, unit::Symbol) where{FT<:Real}
```

座標の回転に基づいてオイラー角から回転行列を計算します。回転の順序は「ロール」→「ピッチ」→「ヨー」であり、すなわち「z軸」→「x軸」→「z軸」の順にそれぞれα、β、γ度回転します [Wikipedia-Euler_angles](https://en.wikipedia.org/wiki/Euler_angles) 入力：α、β、γ、回転角度情報 unit: 入力角度値の単位、デフォルトは:rad、選択肢は:deg 出力：rotMat :: SMatrix{3, 3, FT}、座標回転行列 rotMat * vec は、vecをローカル座標からグローバル座標に変換します
