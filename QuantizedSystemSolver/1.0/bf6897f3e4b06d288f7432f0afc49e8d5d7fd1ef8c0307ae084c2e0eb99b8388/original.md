```
getError(sol::Sol{T,O},index::Int,f::Function) where{T,O}
```

calculates the relative error of one variable of the solution with respect to a function of an analytic solution.

$$
\begin{equation*}
err=\sqrt{\frac{\sum(sol_{index}-f_{index})^2}{\sum(f_{index})^2}}
\end{equation*}
$$
