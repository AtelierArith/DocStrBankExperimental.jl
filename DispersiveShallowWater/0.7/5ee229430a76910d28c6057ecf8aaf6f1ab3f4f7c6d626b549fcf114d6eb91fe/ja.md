```
wave_speed(disp_rel, equations, k; normalize = false)
```

与えられた波数 $k$ に対して、[`LinearDispersionRelation`](@ref) `disp_rel` の波速 $c$ を計算します。波速は $c = \omega(k) / k$ で与えられます。`normalize` が `true` の場合、波速は浅水波の波速 $\sqrt{g h_0}$ で正規化されます。ここで、$g$ は `equations` の重力加速度で、$h_0$ は分散関係 `disp_rel` の `ref_height` です。

[`LinearDispersionRelation`](@ref) も参照してください。
