```
getAverageError(sol::Sol{T,O},f::Vector{Function}) where{T,O}
```

は、解析解の関数ベクトルに対する解のすべての変数の平均相対誤差を計算します。

$$
\begin{align*}
& err_{index}=\sqrt{\frac{\sum(sol_{index}-f_{index})^2}{\sum(f_{index})^2}}\
& avgError=\frac{\sum_{index=1}^{T}err_{index}}{T}
\end{align*}
$$
