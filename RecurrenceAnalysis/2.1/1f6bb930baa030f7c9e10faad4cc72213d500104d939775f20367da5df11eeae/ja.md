```
trend(R[; border=10, theiler])
```

再帰行列 `R` の再帰のトレンドを計算します。

## 説明

トレンドは、LOI に平行な対角線上の再帰点の密度と、それらの対角線と LOI との距離に関連する線形回帰の傾きです。これは、再帰プロットにおいて点が中央対角線から「消えていく」場合、トレンドが負の値を持つことから、システムの定常性の度合いを定量化します。

これは次のように計算されます：

$$
TREND = 10^3\frac{\sum_{d=1+\tau}^{\tilde{N}}\delta[d]\left(RR[d]-\langle RR[d]\rangle\right)}{\sum_{d=1+\tau}^{\tilde{N}}\delta[d]^2}
$$

ここで、$RR[d]$ は対角線 $d$ の局所再帰率、$\tau$ は Theiler ウィンドウ（除外される中央対角線の数）、$\tilde{N}$ は含まれる最外部の対角線の数、$\delta[d]$ はその対角線と LOI との距離のバランスの取れた測定値で、$d-(\tilde{N}+\tau)/2$ に等しいです。

このパラメータは、1000 データポイントごとの変動再帰率の単位で表されるため、式 [1] における因子 $10^3$ が含まれています。

最外部の 10 本の対角線（行列の隅から数えた場合）は、「境界効果」を避けるためにデフォルトで除外されます。異なる数の除外行を定義するにはキーワード引数 `border` を使用し、Theiler ウィンドウのサイズを定義するには `theiler` を使用します（詳細は [`rqa`](@ref) を参照してください）。

*注*: 矩形の交差再帰プロット（すなわち、それらを生成する時系列が同じ長さでない場合）において、TREND の式の限界は明確に定義されていません。一貫性のために、この関数は LOI を含む最大の正方行列に計算を制限します。

## 参考文献

[1] C.L. Webber & J.P. Zbilut, "Recurrence Quantification Analysis of Nonlinear Dynamical Systems", in: Riley MA & Van Orden GC, *Tutorials in Contemporary Nonlinear Methods for the Behavioral Sciences*, 2005, 26-94. https://www.nsf.gov/pubs/2005/nsf05057/nmbs/nmbs.pdf
