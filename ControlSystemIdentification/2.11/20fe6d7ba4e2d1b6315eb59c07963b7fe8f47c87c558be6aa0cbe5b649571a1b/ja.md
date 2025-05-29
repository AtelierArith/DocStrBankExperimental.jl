```
Gtf = arx(d::AbstractIdData, na, nb; inputdelay = ones(Int, size(nb)), λ = 0, estimator=\, stochastic=false)
```

ARXモデルと方程式誤差最小化を使用してデータに転送関数をフィットさせます。

ARXの略語は「外因性入力を持つ自己回帰モデル」を意味します。

  * `nb`と`na`は、それぞれ分子および分母多項式の係数の数です。

入力遅延は`inputdelay = d`を介して追加でき、これは`z^-d`の追加遅延に対応します。`inputdelay = 0`は直接項を生成します。B多項式の最高次数は`nb + inputdelay - 1`で与えられます。`λ > 0`はL₂正則化のために提供できます。`estimator`はデフォルトで\（最小二乗）であり、代替として`estimator = tls`が全最小二乗推定のために使用されます。`arx(Δt,yn,u,na,nb, estimator=wtls_estimator(y,na,nb)`は、重い測定ノイズが存在する場合により堅牢である可能性があります。自由パラメータの数は`na+nb`です。

  * `stochastic`: trueの場合、不確実なパラメータを`MonteCarloMeasurements.Particles`で表現した転送関数を返します。

nb = [nb₁, nb₂...]およびオプションのinputdelay = [d₁, d₂...]を持つ行列`u`を持つiddataを提供することにより、MISO推定をサポートします。

この関数は、iddataオブジェクトのベクトルとして提供される複数のデータセットをサポートします。
