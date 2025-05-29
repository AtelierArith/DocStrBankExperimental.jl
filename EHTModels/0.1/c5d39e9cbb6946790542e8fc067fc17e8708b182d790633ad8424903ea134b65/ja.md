```
RectangleFilter(θmaj, [θmin, ϕ]; [θunit, ϕunit])
```

単位の総フラックス密度を持つ長方形フィルターを作成します。

引数:

  * `θmaj::Real`:   長方形の主軸のサイズ。
  * `θmin::Real`:   長方形の副軸のサイズ。`θmin < 0` の場合、`θmin = θmax`（すなわち正方形）になります。デフォルトは -1。
  * `ϕ::Real`:   長方形の位置角。デフォルトは 0。
  * `θunit, ϕunit::Unitful`:   それぞれ `θmaj` と `θmin` および `ϕ` の単位。デフォルト: `θunit=rad` および `ϕ=deg`。
