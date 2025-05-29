```
surface_velocity(body::Body,motion::AbstractMotion,t::Real[;inertial=true])
```

剛体の速度の成分を返します（慣性座標系において）、時間 `t` における `body` の慣性座標で記述された表面位置で、`motion` に供給された動きに基づいています。`inertial=false` の場合、速度は計算され、剛体の位置は共動座標にあると仮定されます。
