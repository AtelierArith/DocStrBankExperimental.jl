```
getError(sol::Sol{T,O},index::Int,f::Function) where{T,O}
```

は、解析解の関数に対する解の1つの変数の相対誤差を計算します。

$$
\begin{equation*}
err=\sqrt{\frac{\sum(sol_{index}-f_{index})^2}{\sum(f_{index})^2}}
\end{equation*}
$$
