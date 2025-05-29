```
clear_sky(;lat, DOY, t, altitude = 0.0, TL = 4.0)
```

IneichenとPerez（2002）によるクリアスカイモデルを使用して、水平面上の全球、直接および散乱太陽放射を計算します。

# 引数

  * `lat`: 緯度（ラジアン）
  * `DOY`: 年の日
  * `f`: 日の割合（0 = 日の出、1 = 日の入り）
  * `altitude`: 海面上の高度（メートル、デフォルトは0.0）
  * `TL`: リンケ濁度係数（デフォルトは4.0）

# 戻り値

フィールドを持つ名前付きタプル：

  * `Ig`: 水平面上の全球太陽放射（W/m^2）
  * `Idir`: 水平面上の直接太陽放射（W/m^2）
  * `Idif`: 水平面上の散乱太陽放射（W/m^2）
  * `theta`: 太陽天頂角（ラジアン）
  * `phi`: 太陽方位角（ラジアン）

# 参考文献

Ineichen P., Perez R., A new airmass independent formulation for the Linke turbidity coefficient, Solar Energy, Vol 73(3), pp.151–157, 2002.
