```
proper_motion(object, pmotion, parallax, rvelocity, pmt, observer)
```

適切な動き、視差、放射速度、およびローマー補正のための座標を修正します。

# 引数

  * `object::Vector{AbstractFloat}`: 天体のRAとDec（ラジアン単位）
  * `propermo::Vector{AbstractFloat}`: 天体のRAとDecの適切な動き（ラジアン/年）
  * `parallax::AbstractFloat`: 天体の視差（アーク秒単位）
  * `rvelocity::AbsractFloat`: 天体の放射速度（km/秒単位; 正の値は遠ざかることを示す）
  * `propertim::AbstactFloat`: 適切な動きの時間間隔（ユリウス年単位; 重心で）
  * `observer::Vector{AbstractFloat}`: 観測者の位置（AU単位; 重心からの距離）

# 戻り値

  * `object::Vector{AbstractFloat}`: 修正された天体のRAとDec
