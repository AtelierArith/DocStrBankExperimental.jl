```
density_2D( rho::Real, pixelSideLength::Real, 
            Mass::Real=1.989e43, Length::Real=3.085678e21)
```

物理単位での密度を[g/cm^2]で計算します。

## 引数:

  * `rho`: 物理コード単位でのSPH粒子密度。
  * `pixelSideLength`: 物理単位でのピクセルの長さ。
  * `Mass`: [g]での質量単位。
  * `Length`: [cm]での長さ単位。

## マッピング設定

  * 重み関数: [`part_weight_one`](@ref)
  * 画像を縮小: `true`
