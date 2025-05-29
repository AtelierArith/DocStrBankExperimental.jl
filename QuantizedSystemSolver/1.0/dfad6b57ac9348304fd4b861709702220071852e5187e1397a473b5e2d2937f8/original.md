```
getErrorByRefs(sol::Sol{T,O},index::Int,solRef::Vector{Any}) where{T,O}
```

calculates the relative error of one variable of the solution with respect to a vector of values received from a reference solution.

$$
\begin{equation*}
err=\sqrt{\frac{\sum(sol_{index}-solRef_{index})^2}{\sum(solRef_{index})^2}}
\end{equation*}
$$
