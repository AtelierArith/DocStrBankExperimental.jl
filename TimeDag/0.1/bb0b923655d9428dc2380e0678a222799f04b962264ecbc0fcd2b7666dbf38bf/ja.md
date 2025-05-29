```
ema(x::Node, α::AbstractFloat) -> Node
ema(x::Node, w_eff::Integer) -> Node
```

ノードを作成して、`x`の指数移動平均を計算します。

減衰は、`0 < α < 1`を満たす`α`によって指定されるか、1より大きい整数である必要がある`w_eff`によって指定されます。後者が指定された場合、`α = 2 / (w_eff + 1)`を計算します。

内部状態$s_t$について、$s_0 = 0$、および結果のEMA系列$m_t$は次の形になります：

$$
\begin{aligned}
s_t &= s_{t-1} + (1 - \alpha) x_t \\
m_t &= \frac{\alpha s_t}{1 - (1 - \alpha)^t}.
\end{aligned}
$$

詳細については、[Wikipedia](https://en.wikipedia.org/wiki/Moving_average#Exponential_moving_average)の記法の慣習と議論を参照してください。この関数は、初期収束問題の補正を含むバリアントを実装していることに注意してください。
