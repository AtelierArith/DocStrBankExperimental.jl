```
set_state!([x,] system::ExpandedSystem, prescribed_conditions; kwargs...)
```

`system`（またはベクトル `x`）の状態変数を提供された値に設定します。

# キーワード引数

  * `u`: 各点の線形変位を含むベクトル。
  * `theta`: 各点の角変位を含むベクトル。
  * `V`: 変形した点フレーム内の各点の線形速度を含むベクトル。
  * `Omega`: 変形した点フレーム内の各点の角速度を含むベクトル。
  * `F`: 各点に作用する外部から加えられた力を含むベクトル。
  * `M`: 各点に作用する外部から加えられたモーメントを含むベクトル。
  * `F1`: 各ビーム要素の開始時の合成力を含むベクトル（変形した要素フレーム内）。
  * `M1`: 各ビーム要素の開始時の合成モーメントを含むベクトル（変形した要素フレーム内）。
  * `F2`: 各ビーム要素の終了時の合成力を含むベクトル（変形した要素フレーム内）。
  * `M2`: 各ビーム要素の終了時の合成モーメントを含むベクトル（変形した要素フレーム内）。
  * `V_e`: 変形したビーム要素の参照フレーム内の各ビーム要素の線形速度を含むベクトル。
  * `Omega_e`: 変形したビーム要素の参照フレーム内の各ビーム要素の角速度を含むベクトル。
