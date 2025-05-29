```
set_pull_up_down(self::Pi, gpio, pud)
```

ピン `gpio` の内部 GPIO プルアップ/ダウン抵抗を設定またはクリアします（0 から 53 の間の整数）。`pud` の可能な値は `PiGPIO.PUD_UP`、`PiGPIO.PUD_DOWN` または `PiGPIO.PUD_OFF` です。

```julia
set_pull_up_down(pi, 17, PiGPIO.PUD_OFF)
set_pull_up_down(pi, 23, PiGPIO.PUD_UP)
set_pull_up_down(pi, 24, PiGPIO.PUD_DOWN)
```
