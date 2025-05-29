```
getAverageError(sol::Sol{T,O},f::Vector{Function}) where{T,O}
```

calculates the average relative error of all variables of the solution with respect to a vector of functions of analytic solutions.

$$
\begin{align*}
& err_{index}=\sqrt{\frac{\sum(sol_{index}-f_{index})^2}{\sum(f_{index})^2}}\
& avgError=\frac{\sum_{index=1}^{T}err_{index}}{T}
\end{align*}
$$
