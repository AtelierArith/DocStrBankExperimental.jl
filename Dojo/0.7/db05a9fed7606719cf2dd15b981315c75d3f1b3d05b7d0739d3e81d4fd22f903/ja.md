```
Rotational{T} <: Joint{T}

回転自由度を制限する制約

axis: 親オフセットフレームにおける回転軸
axis_mask1: pbodyのフレームにおける回転軸マスク
axis_mask2: pbodyのフレームにおける回転軸マスク
axis_mask3: pbodyのフレームにおける回転軸マスク
orientation_offset: pbodyのフレームからの回転軸オフセット
spring :ジョイントスプリングの係数
damper: ジョイントダンパーの係数
spring_offset: 名目上のジョイント構成
joint_limits: ジョイント構成の下限および上限
spring_type: :linear または :sinusoidal（現在は未実装）である可能性があり、線形の場合は360°の特異点を避けるためにjoint_limitsが必要です。
input: 外部インパルストルク
```
