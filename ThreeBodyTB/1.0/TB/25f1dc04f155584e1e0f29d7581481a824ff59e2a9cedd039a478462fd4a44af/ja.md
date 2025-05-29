```
function calc_bands(h, kpoints::Array{Float64,2}; spin=1)
```

k点配列からのk点のバンド構造を計算します。hは`tb`または`tb_k`オブジェクトです。
