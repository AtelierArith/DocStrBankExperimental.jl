```
Conditionals( distribution :: Matrix{<:Real}; atol=ATOL :: Float64 ) <: ConditionalDistribution
```

A struct representing a conditional probability distribution function. `Conditionals` are organized in a matrix with rows correpsonding to outputs and columns corresponding to inputs. For example if there are $M$ inputs and $N$ outputs, the corresponding conditionals matrix takes the form:

$$
\begin{bmatrix}
p(1|1) & \dots & p(1|M) \\
\vdots & \ddots & \vdots \\
p(N|1) & \dots & p(N|M) \\
\end{bmatrix}
$$
