```
set_mode(pi::Pi, pin::Int, mode)
```

Sets the GPIO `mode` of the given `pin` (integer between 0 and 53) of the Pi instance `pi`. The mode con be `PiGPIO.INPUT`, `PiGPIO.OUTPUT`, `PiGPIO.ALT0`, `PiGPIO.ALT1`, `PiGPIO.ALT2`, `PiGPIO.ALT3`, `PiGPIO.ALT4` or `PiGPIO.ALT5`.

```julia
set_mode(pi,  4, PiGPIO.INPUT)  # GPIO  4 as input
set_mode(pi, 17, PiGPIO.OUTPUT) # GPIO 17 as output
set_mode(pi, 24, PiGPIO.ALT2)   # GPIO 24 as ALT2
```
