```
SIR(du,u,p,t)
```

Define classic SIR(suspected-infected-recovered) model. 

Parameters: (birth rate, natural death rate, disaese induced death rate, population, infection rate, recovery rate)

$$
\begin{aligned}
& \frac{\rm{d}S}{\rm{dt}} = \Lambda -\beta S I/N - d S,\\
&\frac{\rm{d}I}{\rm{dt}} = \beta  S I/N - \gamma I - d I - \alpha I,\\
&\frac{\rm{d}R}{\rm{dt}} = \gamma I - d R,\\
\end{aligned}
$$
