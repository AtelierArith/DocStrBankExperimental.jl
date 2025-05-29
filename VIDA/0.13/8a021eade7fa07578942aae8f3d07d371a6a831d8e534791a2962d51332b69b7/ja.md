```julia
struct KullbackLeibler <: VIDA.AbstractDivergence
```

KLダイバージェンスのための型です。これは`IntensityMap`、すなわちデータから構築されます。さらに、ダイバージェンスを評価するために、θがあなたのものである場合にファンクタアプローチを使用します。

### 詳細

これは、2つの分布間のヘリンガー距離に関連するKLダイバージェンスを計算します。実際、両者は同じ点で最小化されます。バタチャリヤダイバージェンスは次のように定義されます。

$$
KL(f_\theta||\hat{I}) = -\log\int f_{\theta}(x,y)\log
        \left(\frac{f_{\theta}(x,y)}{\hat{I}(x,y)}\right)dxdy,
$$

ここで、$\hat{I}$は単位フラックスに正規化された画像として定義されます。

この構造体もファンクタです。
