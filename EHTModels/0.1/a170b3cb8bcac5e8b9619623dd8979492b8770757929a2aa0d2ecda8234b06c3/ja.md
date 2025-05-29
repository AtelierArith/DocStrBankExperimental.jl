```
EllipticalGaussian(F, θmaj, [θmin, ϕ, x0, y0]; [θunit, ϕunit])
```

楕円ガウス関数を作成します。

引数:

  * `F::Real`:   ガウス関数の総フラックス密度。
  * `θmaj::Real`:   ガウス関数の主軸FWHMサイズ。
  * `θmin::Real`:   ガウス関数の副軸FWHMサイズ。`θmin < 0` の場合、`θmin = θmax`（すなわち円形ガウス関数）になります。デフォルトは -1。
  * `ϕ::Real`:   ガウス関数の位置角。デフォルトは 0。
  * `x0, y0::Real`:   θunitの単位での中心位置。デフォルトは 0。
  * `θunit::Unitful`:   `θmaj`、`θmin`、`x0`、および `y0` の単位。デフォルト: `θunit=rad`。
  * `ϕunit::Unitful`:   `ϕ` の単位。デフォルト: `ϕ=deg`。
