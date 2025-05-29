```
datacharacteristics(d::D2XXDevice; 
                    wordlength::FTWordLength = BITS_8, 
                    stopbits::FTStopBits = STOP_BITS_1, 
                    parity::FTParity = PARITY_NONE)
```

オープンな [`D2XXDevice`](@ref) のために、[`FT_SetDataCharacteristics`](@ref) を使用して送信および受信データの特性を設定します。

# 引数

  * `wordlength::FTWordLength` : BITS*7 または BITS*8
  * `stopbits::FTStopBits` : STOP*BITS*1 または STOP*BITS*2
  * `parity::FTParity` : PARITY*NONE、PARITY*ODD、PARITY*EVEN、PARITY*MARK、または PARITY_SPACE
