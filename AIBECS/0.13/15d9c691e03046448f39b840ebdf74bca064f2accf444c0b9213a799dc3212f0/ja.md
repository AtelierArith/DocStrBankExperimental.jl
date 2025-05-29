```
FATO(w_top, Iabove)
```

粒子の沈降速度 `w_top` のための `FATO` 演算子を構築します。

（`w_top` は各グリッドセルの上部での沈降速度です。）

`FATO` 演算子は次のように定義されます。

```
FATO * x = w_top * x(above) ≈ ϕ_top.
```
