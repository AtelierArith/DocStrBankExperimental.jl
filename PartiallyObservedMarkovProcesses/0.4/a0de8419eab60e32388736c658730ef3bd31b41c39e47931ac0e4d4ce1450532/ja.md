```
gompertz()
```

`gompertz` は *PompObject* で、*Parus major* データと単純なゴンペルツ人口モデルを含んでいます。この人口モデルには、単一のスカラー状態変数 $X_t$ があり、次のように従います。

$$
X_t = X_{t-1}^S\,K^{1-S}\,\varepsilon_t,
$$

ここで、$S = e^{-r\delta{t}}$ であり、$\varepsilon_t \sim \mathrm{LogNormal}(0,\sigma_p)$ です。時間ステップは1単位です：$\delta{t}=1$。データは対数正規分布から抽出されると仮定されています。特に、

$$
\mathrm{pop}_t \sim \mathrm{LogNormal}(\log{X_t},\sigma_m).
$$

## パラメータ

  * r: 成長率
  * K: 平衡人口密度
  * X₀: 初期人口密度
  * σₚ: プロセスノイズの標準偏差
  * σₘ: 測定ノイズの標準偏差
