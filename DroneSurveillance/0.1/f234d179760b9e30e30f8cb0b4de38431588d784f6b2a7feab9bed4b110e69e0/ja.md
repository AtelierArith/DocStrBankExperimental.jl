```
DroneSurveillancePOMDP{M} <: POMDP{DSState, Int64, Int64}
```

# フィールド

  * `size::Tuple{Int64, Int64} = (5,5)` グリッドワールドのサイズ
  * `region_A::DSPos = [1, 1]` 調査する最初の領域、クアッドの初期状態
  * `region_B::DSPos = [size[1], size[2]]` 調査する2番目の領域
  * `fov::Tuple{Int64, Int64} = (3, 3)` ドローンの視野のサイズ
  * `agent_policy::Symbol = :restricted` 他のエージェントのポリシー
  * `camera::M = QuadCam()` 観測モデル、完璧なカメラとクアッドカメラの間で選択
  * `terminal_state::DSState = DSState([-1, -1], [-1, -1])` 終端状態をエンコードするためのセンチネル状態
  * `discount_factor::Float64 = 0.95` 割引率
