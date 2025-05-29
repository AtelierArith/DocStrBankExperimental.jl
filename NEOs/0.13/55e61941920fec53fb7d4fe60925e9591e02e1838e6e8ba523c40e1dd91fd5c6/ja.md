```
loadpeeph(eph::TaylorInterpolant = sseph, t_0::T = sseph.t0,
          t_f::S = sseph.t0 + sseph.t[end]) where {T, S <: Real}
```

`PlanetaryEphemeris.jl`によって生成されたエフェメリスを、タイムレンジ`[t_0, t_f] ⊆ [0.0, 36525.0]`でロードします。ここで`t`はJ2000からのTDB日数の単位を持つ必要があります。`eph`の利用可能なオプションは次のとおりです：

  * `NEOs.sseph`: 太陽系エフェメリス。
  * `NEOs.acceph`: 加速度エフェメリス。
  * `NEOs.poteph`: ニュートンポテンシャルエフェメリス。

!!! warning
    この関数を初めて実行すると、`sseph_p100`アーティファクト（885 MB）がダウンロードされ、数分かかることがあります。

