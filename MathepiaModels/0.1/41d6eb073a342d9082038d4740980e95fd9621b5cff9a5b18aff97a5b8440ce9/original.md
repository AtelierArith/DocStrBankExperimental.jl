```
SIS(du,u,p,t)
```

Define classic SIR(suspected-infected-suspected) model. 

Parameters: (population, infection rate, recovery rate)

$$
\begin{aligned}
& \frac{\rm{d}S}{\rm{dt}} = -\beta S I/N + \gamma I,\\
&\frac{\rm{d}I}{\rm{dt}} = \beta  S I/N - \gamma I,\\
\end{aligned}
$$
