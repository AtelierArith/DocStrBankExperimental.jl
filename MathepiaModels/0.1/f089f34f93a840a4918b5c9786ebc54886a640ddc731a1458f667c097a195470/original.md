```
SEIAR(du,u,p,t)
```

Define classic SEIR(suspected-exposed-infected-asymptomatic-recovered) model. 

Parameters: (birth rate, natural death rate, disaese induced death rate, population, infection rate, recovery rate, incubation period, exposed decreasing infection ratio, asymptomatic infection decreasing infection ratio, asymptomatic rate,recovery rate of asymptomatic)

$$
\begin{aligned}
& \frac{\rm{d}S}{\rm{dt}} = \Lambda -\beta S (I+k_{E}E+k_{A}A)/N - d S,\\
&\frac{\rm{d}E}{\rm{dt}} = \beta  S (I+k_{E}E++k_{A}A)/N - \sigma E -d E,\\
&\frac{\rm{d}I}{\rm{dt}} =(1-\rho)\sigma E - \gamma I - d I - \alpha I,\\
&\frac{\rm{d}A}{\rm{dt}} =\rho\sigma E - \gamma_{A} A - d A,\\
&\frac{\rm{d}R}{\rm{dt}} = \gamma I +\gamma_{A} A - d R,\\
\end{aligned}
$$
