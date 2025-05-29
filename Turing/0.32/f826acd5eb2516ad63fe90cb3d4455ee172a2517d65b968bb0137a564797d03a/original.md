```
OrderedLogistic(η, c::AbstractVector)
```

The *ordered logistic distribution* with real-valued parameter `η` and cutpoints `c` has the probability mass function

$$
P(X = k) = \begin{cases}
    1 - \text{logistic}(\eta - c_1) & \text{if } k = 1, \\
    \text{logistic}(\eta - c_{k-1}) - \text{logistic}(\eta - c_k) & \text{if } 1 < k < K, \\
    \text{logistic}(\eta - c_{K-1}) & \text{if } k = K,
\end{cases}
$$

where `K = length(c) + 1`.
