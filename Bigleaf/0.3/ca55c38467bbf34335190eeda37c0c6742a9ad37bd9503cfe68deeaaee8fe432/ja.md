```
Gb_constant_kB1(ustar, kB_h; constants)
compute_Gb!(df, ::ConstantKB1})
```

境界層伝導率は、熱伝達のための定数 kB^(-1) 値を使用します。

# 引数

  * `ustar`     : 摩擦速度 (m s-1)
  * `df`        : 上記の変数を含む DataFrame
  * `kB_h`      : 熱伝達のための kB^(-1) 値
  * `constants=`[`BigleafConstants`](@ref)`()`

# 詳細

Rb*h は ``kB*h/(k * ustar)`` によって計算され、ここで k はフォン・カルマン定数です。
