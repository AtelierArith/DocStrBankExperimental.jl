```
ema(x::Node, α::AbstractFloat) -> Node
ema(x::Node, w_eff::Integer) -> Node
```

Create a node which computes the exponential moving average of `x`.

The decay is specified either by `α`, which should satisfy `0 < α < 1`, or by `w_eff`, which should be an integer greater than 1. If the latter is specified, then we compute `α = 2 / (w_eff + 1)`.

For internal state $s_t$, with $s_0 = 0$, and resulting EMA series $m_t$, this has the form:

$$
\begin{aligned}
s_t &= s_{t-1} + (1 - \alpha) x_t \\
m_t &= \frac{\alpha s_t}{1 - (1 - \alpha)^t}.
\end{aligned}
$$

For further information, see the notational conventions and discussion on [Wikipedia](https://en.wikipedia.org/wiki/Moving_average#Exponential_moving_average). Note that this function implements the variant including the correction for the initial convergence problem.
