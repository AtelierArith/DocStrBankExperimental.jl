```
Conditionals( distribution :: Matrix{<:Real}; atol=ATOL :: Float64 ) <: ConditionalDistribution
```

条件付き確率分布関数を表す構造体です。`Conditionals`は、出力に対応する行と入力に対応する列を持つ行列に整理されています。例えば、$M$個の入力と$N$個の出力がある場合、対応する条件付き行列は次の形になります：

$$
\begin{bmatrix}
p(1|1) & \dots & p(1|M) \\
\vdots & \ddots & \vdots \\
p(N|1) & \dots & p(N|M) \\
\end{bmatrix}
$$
