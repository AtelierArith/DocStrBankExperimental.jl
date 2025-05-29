```
mutable struct RateLimiter
```

出力信号の変化率（`calc_output`の戻り値）を± limitに制限します。制限の単位：1/s。

## フィールド

  * `dt::Float64`: デフォルト: 0.05
  * `limit::Float64`: デフォルト: 1
  * `output::Float64`: デフォルト: 0
  * `last_output::Float64`: デフォルト: 0

# 例

```julia
using WinchControllers, ControlPlots
rl = RateLimiter(1.0, 0.8)
input =  [0,0,1,2,3,3,3,3,3,2,1,0,0,0,0,0]
out = zeros(16)
for i in 1:16
    out[i] = calc_output(rl, input[i])
    on_timer(rl)
end
plot(1:16, [input, out]; labels=["input", "output"])
```

![rate_limiter](assets/rate_limiter.png).
