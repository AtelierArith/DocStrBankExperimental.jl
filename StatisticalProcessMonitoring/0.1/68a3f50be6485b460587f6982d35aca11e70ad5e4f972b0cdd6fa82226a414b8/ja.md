```
OneSidedCurvedLimit(h::Float64, upw::Bool)
OneSidedCurvedLimit(h::Vector{T}, upw::Vector{Bool})
```

曲線の片側制限であり、制御チャートのラン長 $RL$ は、統計量 $C_t$ が制限を超える最初の時刻 $t$ です。

  * `upw == true` の場合、$RL = \inf\{t : C_t > h\cdot f(t)\}$
  * `upw == false` の場合、$RL = \inf\{t : C_t < -h\cdot f(t)\}$

定義により、$h > 0$ であることに注意してください。
