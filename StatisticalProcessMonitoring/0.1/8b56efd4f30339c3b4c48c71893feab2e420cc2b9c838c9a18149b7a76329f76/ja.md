```
TwoSidedCurvedLimit(h::Float64)
TwoSidedCurvedLimit(h::Vector{T})
```

曲線の片側限界であり、制御チャートの走行長 $RL$ は統計量 $C_t$ が限界を超える最初の時間 $t$ です。

$$
RL = \inf\{t > 0 : |C_t| > h\cdot f(t)\}
$$

。

定義により、$h > 0$ であることに注意してください。
