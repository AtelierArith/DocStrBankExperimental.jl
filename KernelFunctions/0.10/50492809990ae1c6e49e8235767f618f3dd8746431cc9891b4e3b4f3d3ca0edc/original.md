```
PeriodicKernel(; r::AbstractVector=ones(Float64, 1))
```

Periodic kernel with parameter `r`.

# Definition

For inputs $x, x' \in \mathbb{R}^d$, the periodic kernel with parameter $r_i > 0$ is defined[^DM] as

$$
k(x, x'; r) = \exp\bigg(- \frac{1}{2} \sum_{i=1}^d \bigg(\frac{\sin\big(\pi(x_i - x'_i)\big)}{r_i}\bigg)^2\bigg).
$$

[^DM]: D. J. C. MacKay (1998). Introduction to Gaussian Processes.
