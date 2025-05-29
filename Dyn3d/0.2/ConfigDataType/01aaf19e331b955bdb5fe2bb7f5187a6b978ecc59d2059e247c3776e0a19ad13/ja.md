```
Motions(type::String, parameters::Vector{Float64})
```

関節のアクティブモーションを表す構造体で、異なるタイプのモーションを許可し、時間依存であることができます。

## フィールド

  * `motion_type`: "hold", "velocity*const", "velocity*linear", "oscillatory", "ramp*1", "ramp*2" の選択を許可
  * `motion_params`: モーションを説明するために提供される数値パラメータ

## コンストラクタ

  * `Motions(): アクティブモーションを提供しない`
  * `Motions("hold", [qJ])`: 関節を一定の qJ で保持し、vJ=0
  * `Motions("velocity_const",[qJ,vJ])`: 初期角度 qJ でこの関節の一定の vJ を指定
  * `Motions("velocity_linear",[qJ,vJ,aJ])`: 初期角度 qJ と初期角速度 vJ でこの関節の一定の加速度 aJ を指定し、指定された角速度は線形です
  * `Motions("oscillatory",[amp,freq,phase])`: $qJ = amp*cos(2π*freq*t+phase)$ を通じて振動モーションを指定
  * `Motions("ramp_1",[a,t₁,t₂,t₃,t₄])`: [^1] におけるランプモーションを説明
  * `Motions("ramp_2",[a])`: 初期速度を持つ減速モーションを説明

[^1]: Eldredge, Jeff, Chengjie Wang, and Michael Ol. "A computational study of a canonical pitch-up,

pitch-down wing maneuver." In 39th AIAA fluid dynamics conference, p. 3687. 2009.

## 関数

  * `(m::Motions)(t)`: 時間 t におけるモーションタイプを評価し、関節角 qJ と速度 vJ を返す
