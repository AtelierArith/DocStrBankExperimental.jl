```
contour(f; options...)
```

アモエバ $\mathcal{A}(f)$ の輪郭 𝐶(𝑓) を計算します。

## 例

```julia
@polyvar x y

contour(x^2+y^2+1)

# カスタムドメイン
contour(x^2+y^2+1, domain=(-5, 5, -5, 5))
```

## オプション

  * `domain`: 輪郭 𝐶(𝑓) が計算されるセクション Ω を定義する形式 `(xmin, xmax, ymin, ymax)` のタプル。
  * `membership_options`: メンバーシップテストのオプション
  * `res=(600,600)`: 開始点がサンプリングされる解像度
  * `samples_off_axis=2*MP.maxdegree(p)^2`: オフ軸ごとのサンプルポイントの数。
