```
energy(self::FEMMHeatDiff, geom::NodalField{GFT},  temp::NodalField{FT}) where {GFT, FT}
```

内部領域における「エネルギー」積分を計算します。

「エネルギー」密度は、温度の勾配と熱フラックスのドット積です。

# 引数

  * `self` = モデルマシン,
  * `geom` = 幾何学フィールド,
  * `temp` = 温度フィールド
