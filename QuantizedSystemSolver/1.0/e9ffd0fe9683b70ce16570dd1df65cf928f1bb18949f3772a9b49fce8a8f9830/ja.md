```
getAverageErrorByRefs(sol::Sol{T,O},solRef::Vector{Any}) where{T,O}
```

は、参照解に対する解の平均相対誤差を計算します。相対誤差は各変数について計算され、その後すべての変数にわたって平均化されます。

$$
\begin{align*}
& err_{index}=\sqrt{\frac{\sum(sol_{index}-solRef_{index})^2}{\sum(solRef_{index})^2}}\
& avgError=\frac{\sum_{index=1}^{T}err_{index}}{T}
\end{align*}
$$
