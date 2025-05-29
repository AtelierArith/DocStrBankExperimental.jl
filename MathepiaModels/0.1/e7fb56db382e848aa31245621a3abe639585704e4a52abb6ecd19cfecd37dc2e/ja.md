```
SEIR(du,u,p,t)
```

古典的なSEIR（疑似-曝露-感染-回復）モデルを定義します。

パラメータ：（出生率、自然死率、病気による死亡率、人口、感染率、回復率、潜伏期間、曝露による感染減少比）

$$
\begin{aligned}
& \frac{\rm{d}S}{\rm{dt}} = \Lambda -\beta S (I+k_{E}E)/N - d S,\\
&\frac{\rm{d}E}{\rm{dt}} = \beta  S (I+k_{E}E)/N - \sigma E -d E,\\
&\frac{\rm{d}I}{\rm{dt}} =\sigma E - \gamma I - d I - \alpha I,\\
&\frac{\rm{d}R}{\rm{dt}} = \gamma I - d R,\\
\end{aligned}
$$
