```
mutable struct Winch
```

コンポーネントで、テザーの力と設定された速度（= 同期速度）に基づいてテザーの加速度を計算します。非同期モーターモデルとドラム慣性が考慮されています。ウインチコントローラーのテストに使用されます。

## フィールド

  * `wcs::WinchControllers.WCSettings`
  * `set::KiteUtils.Settings`
  * `wm::WinchModels.AsyncMachine`: デフォルト: AsyncMachine(set)
  * `v_set::Float64`: デフォルト: 0
  * `force::Float64`: デフォルト: 0
  * `acc::Float64`: デフォルト: 0
  * `speed::Float64`: デフォルト: 0
