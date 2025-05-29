```
getErrorByRefs(sol::Sol{T,O},index::Int,solRef::Vector{Any}) where{T,O}
```

は、参照解から受け取った値のベクトルに対する解の1つの変数の相対誤差を計算します。

$$
\begin{equation*}
err=\sqrt{\frac{\sum(sol_{index}-solRef_{index})^2}{\sum(solRef_{index})^2}}
\end{equation*}
$$
