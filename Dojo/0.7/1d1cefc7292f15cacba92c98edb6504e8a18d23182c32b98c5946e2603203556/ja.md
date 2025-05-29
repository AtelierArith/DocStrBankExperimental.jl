```
Translational{T} <: Joint{T}

移動自由度を制限する制約

axis: 親オフセットフレームにおける移動軸
axis_mask1: pbodyのフレームにおける移動軸マスク
axis_mask2: pbodyのフレームにおける移動軸マスク
axis_mask3: pbodyのフレームにおける移動軸マスク
vertices: 親および子フレームの点
spring: ジョイントスプリングの係数
damper: ジョイントダンパーの係数
spring_offset: 標準的なジョイント構成
joint_limits: ジョイント構成の下限および上限
spring_type: :linear または :sinusoidal（現在は未実装）である可能性があり、線形の場合は360°の特異点を避けるためにjoint_limitsが必要です。
input: 外部インパルス力
```
