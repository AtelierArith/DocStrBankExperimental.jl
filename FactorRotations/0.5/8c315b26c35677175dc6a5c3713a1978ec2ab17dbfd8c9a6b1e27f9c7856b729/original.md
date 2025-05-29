```
LinearRightConstant(bandwidth)
```

The linear right constant [component loss](@ref AbstractComponentLoss) factor rotation criterion. It has the loss function

$$
h(\lambda) = \begin{cases}
    (\frac{\lambda}{b})^2&\text{if } |\lambda| \leq b \\
    1 &\text{if } |\lambda| > b,
\end{cases}
$$

where $b$ is the *bandwidth* parameter.
