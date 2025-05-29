```
body_accelerations(system, x=system.x; linear_acceleration=zeros(3), angular_acceleration=zeros(3))
```

状態ベクトルからボディフレームの線形加速度と角加速度を抽出します。該当しない場合は、提供された線形加速度と角加速度を返します。この関数は定常状態および初期条件分析にのみ適用可能です。
