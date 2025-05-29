```
OneSidedFixedLimit(h::Float64, upw::Bool)
```

古典的な片側固定限界であり、制御チャートのラン長 $RL$ は統計量 $C_t$ が限界を越える最初の時刻 $t$ です。

  * `upw == true` の場合、$RL = \inf\{t : C_t > h\}$
  * `upw == false` の場合、$RL = \inf\{t : C_t < -h\}$

定義により、$h > 0$ であることに注意してください。
