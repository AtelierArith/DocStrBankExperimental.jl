```
CoordinateDistortion(DM::AbstractDataModel, Confnum::Real=1) -> Real
```

CoordinateDistortionが1未満のとき、モデルの予測はパラメータに対して非常に敏感です。CoordinateDistortionが1以上のとき、モデルはパラメータに対して比較的鈍感です。

この量は、信頼領域の座標依存の見かけの体積と、適切な体積形式/幾何学的密度因子を用いて得られる座標不変の体積との比率から計算されます。この量の単位は$[L^n]$であり、ここで$L$は各成分の長さの単位です。
