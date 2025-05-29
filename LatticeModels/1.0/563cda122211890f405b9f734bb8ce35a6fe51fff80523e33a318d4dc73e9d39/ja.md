```
GaugeField <: AbstractField
```

ベクトルポテンシャル関数によって定義されたゲージ場。

---

```
GaugeField(func; n)
```

与えられたベクトルポテンシャル関数 `func` を持つゲージ場を作成します。

## 引数

  * `func`: 空間の点を受け取り、この点でのベクトルポテンシャルを `SVector` または `Tuple` として返す関数。
  * `n`: 台形法積分に使用するステップ数。

## 例

```julia
field = GaugeField(n = 10) do p
    (-0.5 * p[2], 0.5 * p[1], 0)
end
```
