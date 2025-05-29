```
VerticalJet{<:Number}(;kwargs...)<:Release
```

垂直ジェット放出のパラメータのためのシンプルなコンテナ。

# 引数

  * `mass_rate::Number`: 物質の質量放出率、kg/s。
  * `duration::Number`: 放出の持続時間、s。
  * `diameter::Number`: ジェットの直径、m。
  * `velocity::Number`: ジェットの平均速度、m/s。
  * `height::Number`: ジェット中心の高さ、m。
  * `pressure::Number`: ジェット出口の圧力、Pa。
  * `temperature::Number`: ジェット出口の温度、K。
  * `fraction_liquid::Number`: 放出のうち液体の割合（気体-液体混合物の場合）、体積割合。
