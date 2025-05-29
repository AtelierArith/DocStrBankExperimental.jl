```
zj = ZudkevitchJoffe(; F_a = (T, c_i) -> 1.0, F_b = (T, c_i) -> 1.0)
```

GenericCubicEOSをZudkevitch-Joffe立方体状態方程式に特化します。

Zudkevitch-Joffe状態方程式は、`weight_ai`および`weight_bi`関数を修正する温度の成分ごとの関数を許可します。これらの追加のフィッティングパラメータは、複雑な混合物に合わせる際の柔軟性を高めます。
