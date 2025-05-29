```
datacharacteristics(handle::FT_HANDLE;
                    wordlength::FTWordLength = BITS_8, 
                    stopbits::FTStopBits = STOP_BITS_1, 
                    parity::FTParity = PARITY_NONE)
```

Set the transmission and reception data characteristics for an open  [`FT_HANDLE`](@ref) using [`FT_SetDataCharacteristics`](@ref).

See also: [`isopen`](@ref), [`open`](@ref)
