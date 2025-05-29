```
SEIR(du,u,p,t)
```

Define classic SEIR(suspected-exposed-infected-recovered) model. 

Parameters: (birth rate, natural death rate, disaese induced death rate, population, infection rate, recovery rate, incubation period, exposed decreasing infection ratio)

$$
\begin{aligned}
& \frac{\rm{d}S}{\rm{dt}} = \Lambda -\beta S (I+k_{E}E)/N - d S,\\
&\frac{\rm{d}E}{\rm{dt}} = \beta  S (I+k_{E}E)/N - \sigma E -d E,\\
&\frac{\rm{d}I}{\rm{dt}} =\sigma E - \gamma I - d I - \alpha I,\\
&\frac{\rm{d}R}{\rm{dt}} = \gamma I - d R,\\
\end{aligned}
$$
