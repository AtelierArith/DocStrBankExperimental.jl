```julia
struct Bhattacharyya <: VIDA.AbstractDivergence
```

Bhattacharyyaダイバージェンスの型です。これは`IntensityMap`、すなわちデータから構築されます。さらに、ダイバージェンスを評価するために、θがあなたのものである場合にファンクタアプローチを使用します。

### 詳細

これは、2つの分布間のヘリンガー距離に関連するバッタチャリヤダイバージェンスを計算します。実際、両者は同じ点で最小化されます。バッタチャリヤダイバージェンスは次のように定義されます。

$$
Bh(f_\theta||\hat{I}) = -\log\int \sqrt{f_\theta(x,y)\hat{I}(x,y)}dxdy,
$$

ここで、$\hat{I}$は単位フラックスに正規化された画像として定義されます。
