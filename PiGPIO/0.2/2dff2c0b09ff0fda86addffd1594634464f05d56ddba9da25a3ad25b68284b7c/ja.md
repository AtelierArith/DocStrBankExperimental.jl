```
set_mode(pi::Pi, pin::Int, mode)
```

指定された `pin`（0から53の間の整数）のGPIO `mode`をPiインスタンス`pi`に設定します。モードは`PiGPIO.INPUT`、`PiGPIO.OUTPUT`、`PiGPIO.ALT0`、`PiGPIO.ALT1`、`PiGPIO.ALT2`、`PiGPIO.ALT3`、`PiGPIO.ALT4`または`PiGPIO.ALT5`にすることができます。

```julia
set_mode(pi,  4, PiGPIO.INPUT)  # GPIO  4を入力として設定
set_mode(pi, 17, PiGPIO.OUTPUT) # GPIO 17を出力として設定
set_mode(pi, 24, PiGPIO.ALT2)   # GPIO 24をALT2として設定
```
