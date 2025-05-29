```
getAverageErrorByRefs(sol::Sol{T,O},solRef::Vector{Any}) where{T,O}
```

calculates the average relative error of the solution with respect to a reference solution. The relative error is calculated for each variable, and then it is averaged over all variables.

$$
\begin{align*}
& err_{index}=\sqrt{\frac{\sum(sol_{index}-solRef_{index})^2}{\sum(solRef_{index})^2}}\
& avgError=\frac{\sum_{index=1}^{T}err_{index}}{T}
\end{align*}
$$
