```
LineIntegralGaugeField <: AbstractField
```

線積分関数によって定義されたゲージ場。

---

```
LineIntegralGaugeField(func)
```

与えられた線積分関数 `func` を持つゲージ場を作成します。この関数は空間内の2点を受け取り、これらの点の間のベクトルポテンシャルの線積分を返す必要があります。

## 例

```julia
field = LineIntegralGaugeField() do p1, p2
    0.5 * (p1[1] * p2[2] - p1[2] * p2[1])   # A = [-y/2, x/2, 0]
end
```
