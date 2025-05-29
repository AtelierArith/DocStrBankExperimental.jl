```
create_filter(AbstractModel, θmaj, [θmin, ϕ]; [θunit, ϕunit]) => AbstractModel
```

与えられた入力ベースモデルを引き伸ばし、回転させることでフィルタモデルを作成します。

引数:

  * `θmaj::Real`:   長軸のサイズ。
  * `θmin::Real`:   短軸のサイズ。`θmin < 0` の場合、`θmin = θmax`（すなわち正方形）になります。デフォルトは -1。
  * `ϕ::Real`:   長方形の位置角。デフォルトは 0。
  * `θunit, ϕunit::Unitful`:   それぞれ `θmaj` と `θmin` および `ϕ` の単位。デフォルト: `θunit=rad` および `ϕ=deg`。
