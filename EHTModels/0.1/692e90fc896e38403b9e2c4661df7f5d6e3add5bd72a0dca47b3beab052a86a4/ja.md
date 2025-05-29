```
CircularGaussian(F, θmaj, [x0, y0]; [θunit, ϕunit])
```

円形ガウスを作成します。

引数:

  * `F::Real`:   ガウスの総フラックス密度。
  * `θfwhm::Real`:   ガウスのFWHMサイズ。
  * `x0, y0::Real`:   θunitの単位での中心位置。デフォルトは0。
  * `θunit::Unitful`:   `θ`、`x0`、および`y0`の単位。デフォルト: `θunit=rad`。
