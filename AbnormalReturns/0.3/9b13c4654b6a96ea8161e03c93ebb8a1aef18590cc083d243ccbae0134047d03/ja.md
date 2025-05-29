```
alpha(rr::RegressionModel, coefname::String...="intercept")
```

CAPMモデルにおける「アルファ」、すなわちモデルの切片です。これは推定期間からのアルファです。

この関数は、提供された係数名の位置を見つけ、デフォルトは「intercept」です。もしcoefnameが回帰に存在しない場合、この関数はエラーを返します。
