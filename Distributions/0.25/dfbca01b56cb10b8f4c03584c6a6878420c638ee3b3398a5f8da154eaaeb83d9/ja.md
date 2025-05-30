```
Chernoff()
```

*チェルノフ分布*は、確率変数の分布です。

$$
\underset{t \in (-\infty,\infty)}{\arg\max} ( G(t) - t^2 ),
$$

ここで、$G$は標準の両側ブラウン運動です。

この分布は、ブランクの単調回帰推定量、グレナンダーの単調密度推定量、ルーセウの最小中央値二乗推定量、マンスキの最大スコア推定量を含む、さまざまな立方根n一貫推定量の極限分布として現れます。

理論的結果については、例えば、キムとポラードの1990年の『Annals of Statistics』を参照してください。pdfおよびcdfの計算のためのコードは、グローネブームとウェルナーの2001年の『Journal of Computational and Graphical Statistics』に記載されたアルゴリズムに基づいています。

```julia
cdf(Chernoff(),-x)              # 尾部確率のためには、1-cdf(Chernoff(),x)の代わりにこれを使用してください
```
