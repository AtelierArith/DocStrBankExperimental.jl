```
SIR(du,u,p,t)
```

古典的なSIR（疑似感染-感染-回復）モデルを定義します。

パラメータ：（出生率、自然死率、病気による死亡率、人口、感染率、回復率）

$$
\begin{aligned}
& \frac{\rm{d}S}{\rm{dt}} = \Lambda -\beta S I/N - d S,\\
&\frac{\rm{d}I}{\rm{dt}} = \beta  S I/N - \gamma I - d I - \alpha I,\\
&\frac{\rm{d}R}{\rm{dt}} = \gamma I - d R,\\
\end{aligned}
$$
