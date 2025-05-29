```
SEIAR(du,u,p,t)
```

古典的なSEIR（疑似感染-曝露-感染-無症状-回復）モデルを定義します。

パラメータ：（出生率、自然死率、病気による死亡率、人口、感染率、回復率、潜伏期間、曝露による感染減少比率、無症状感染による感染減少比率、無症状率、無症状の回復率）

$$
\begin{aligned}
& \frac{\rm{d}S}{\rm{dt}} = \Lambda -\beta S (I+k_{E}E+k_{A}A)/N - d S,\\
&\frac{\rm{d}E}{\rm{dt}} = \beta  S (I+k_{E}E++k_{A}A)/N - \sigma E -d E,\\
&\frac{\rm{d}I}{\rm{dt}} =(1-\rho)\sigma E - \gamma I - d I - \alpha I,\\
&\frac{\rm{d}A}{\rm{dt}} =\rho\sigma E - \gamma_{A} A - d A,\\
&\frac{\rm{d}R}{\rm{dt}} = \gamma I +\gamma_{A} A - d R,\\
\end{aligned}
$$
