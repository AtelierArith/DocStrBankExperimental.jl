```
datacharacteristics(handle::FT_HANDLE;
                    wordlength::FTWordLength = BITS_8, 
                    stopbits::FTStopBits = STOP_BITS_1, 
                    parity::FTParity = PARITY_NONE)
```

オープンされた [`FT_HANDLE`](@ref) のために、[`FT_SetDataCharacteristics`](@ref) を使用して送信および受信データの特性を設定します。

関連情報: [`isopen`](@ref), [`open`](@ref)
