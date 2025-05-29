```
datacharacteristics(d::D2XXDevice; 
                    wordlength::FTWordLength = BITS_8, 
                    stopbits::FTStopBits = STOP_BITS_1, 
                    parity::FTParity = PARITY_NONE)
```

Set the transmission and reception data characteristics for an open  [`D2XXDevice`](@ref) using [`FT_SetDataCharacteristics`](@ref).

# Arguments

  * `wordlength::FTWordLength` : Either BITS*7 or BITS*8
  * `stopbits::FTStopBits` : Either STOP*BITS*1 or STOP*BITS*2
  * `parity::FTParity` : PARITY*NONE, PARITY*ODD, PARITY*EVEN, PARITY*MARK, or  PARITY_SPACE
