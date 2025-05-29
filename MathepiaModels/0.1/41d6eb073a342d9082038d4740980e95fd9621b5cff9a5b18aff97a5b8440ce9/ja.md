```
SIS(du,u,p,t)
```

古典的なSIR（疑似感染者-感染者-疑似感染者）モデルを定義します。

パラメータ：（人口、感染率、回復率）

$$
\begin{aligned}
& \frac{\rm{d}S}{\rm{dt}} = -\beta S I/N + \gamma I,\\
&\frac{\rm{d}I}{\rm{dt}} = \beta  S I/N - \gamma I,\\
\end{aligned}
$$
