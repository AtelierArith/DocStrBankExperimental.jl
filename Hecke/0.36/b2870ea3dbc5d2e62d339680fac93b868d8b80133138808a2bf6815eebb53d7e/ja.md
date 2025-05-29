```
ray_class_field(m::MapClassGrp) -> ClassField
ray_class_field(m::MapRayClassGrp) -> ClassField
```

マップ $m: A \to I$ によって定義される（形式的な）アーベル拡張を作成します。ここで、$I$ は $m$ を定義するモジュラスと互いに素なイデアルの集合であり、$A$ はレイ類群（または類群）の商です。マップ $m$ は {class*group} または {ray*class_group} への呼び出しから返されるマップでなければなりません。
