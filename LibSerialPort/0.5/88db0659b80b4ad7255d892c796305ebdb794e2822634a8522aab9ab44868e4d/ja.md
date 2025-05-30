```
set_frame(sp::SerialPort;
          ndatabits::Integer = 8,
          parity::SPParity   = SP_PARITY_NONE,
          nstopbits::Integer = 1)
```

[data framing](https://en.wikipedia.org/wiki/Universal_asynchronous_receiver/transmitter#Data_framing) パラメータを設定します。デフォルトは非常に一般的な「8N1」方式で、スタートビットの後に8ビットのデータビットが続き、パリティビットはなく、ストップビットが1つあります。

詳細については以下を参照してください。

  * `ndatabits` はデータビットの数で、一般的な「8N1」方式では `8` です。
  * `parity` はパリティビットの存在と値を制御し、`SP_PARITY_NONE`（デフォルト）、`SP_PARITY_ODD`、`SP_PARITY_EVEN`、`SP_PARITY_MARK`、および `SP_PARITY_SPACE` の値を取ることができます。
  * `nstopbits` はストップビットの数を設定し、通常は `1`（デフォルト）または `2` です。
