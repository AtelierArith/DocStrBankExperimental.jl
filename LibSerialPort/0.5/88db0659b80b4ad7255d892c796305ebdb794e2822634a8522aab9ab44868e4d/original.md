```
set_frame(sp::SerialPort;
          ndatabits::Integer = 8,
          parity::SPParity   = SP_PARITY_NONE,
          nstopbits::Integer = 1)
```

Configure the [data framing](https://en.wikipedia.org/wiki/Universal_asynchronous_receiver/transmitter#Data_framing) parameters. Defaults to the very common “8N1” scheme, which consists of a start bit followed by eight data bits, no parity bit, one stop bit.

for more details.

  * `ndatabits` is the number of data bits, which is `8` in the common "8N1" scheme
  * `parity` controls the presence and value of a party bit and can take the values `SP_PARITY_NONE` (default), `SP_PARITY_ODD`, `SP_PARITY_EVEN`, `SP_PARITY_MARK` and `SP_PARITY_SPACE`
  * `nstopbits` sets the number of stop bits, typically `1` (default) or `2`
