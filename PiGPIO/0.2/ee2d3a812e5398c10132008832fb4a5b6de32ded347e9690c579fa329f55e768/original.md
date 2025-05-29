```
set_pull_up_down(self::Pi, gpio, pud)
```

Sets or clears the internal GPIO pull-up/down resistor for the pin `gpio` (integer between 0 and 53). Possible values for `pud` are `PiGPIO.PUD_UP`, `PiGPIO.PUD_DOWN` or `PiGPIO.PUD_OFF`.

```julia
set_pull_up_down(pi, 17, PiGPIO.PUD_OFF)
set_pull_up_down(pi, 23, PiGPIO.PUD_UP)
set_pull_up_down(pi, 24, PiGPIO.PUD_DOWN)
```
