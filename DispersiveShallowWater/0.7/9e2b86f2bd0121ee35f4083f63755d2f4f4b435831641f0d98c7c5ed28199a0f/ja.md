```
LinearDispersionRelation(ref_height)
```

線形分散関係 $\omega(k)$ を表す構造体です。参照水深 $h_0$ は `ref_height` で与えられます。分散関係は `disp_rel(equations, k)` として呼び出すことができ、与えられた波数 `k` と一連の方程式に対して波の周波数 $\omega(k)$ を計算します。

線形分散関係に基づいて波の速度 $c = \omega(k) / k$ を計算するには、[`wave_speed`](@ref) も参照してください。
