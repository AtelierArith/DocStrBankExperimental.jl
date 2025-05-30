```
set_flow_control(sp::SerialPort;
                 rts::SPrts = SP_RTS_OFF,
                 cts::SPcts = SP_CTS_IGNORE,
                 dtr::SPdtr = SP_DTR_OFF,
                 dst::SPdsr = SP_DSR_IGNORE,
                 xonxoff::SPXonXoff = SP_XONXOFF_DISABLED)`
```

Configure the flow-control lines and method. Many systems don't support all options. If an unsupported option is requested, the library will return SP*ERR*SUPP.

  * `rts` controls the output line *Ready To Send (RTS)* and can take the values `SP_RTS_OFF` (default), `SP_RTS_ON` and `SP_RTS_FLOW_CONTROL`.
  * `cts` controls the input line *Clear To Send (CTS)* and can take the values `SP_CTS_IGNORE` (default) and `SP_CTS_FLOW_CONTROL`
  * `dtr` controls the output line *Data Terminal Ready (DTR)* and can take the values `SP_DTR_OFF` (default), `SP_DTR_ON`, and `SP_DTR_FLOW_CONTROL`
  * `dsr` controls the input line *Data Set Ready (DSR)* and can take the values `SP_DSR_IGNORE` (default) and `SP_DSR_FLOW_CONTROL`
  * `xonxoff` controls whether [software flow control](https://en.wikipedia.org/wiki/Software_flow_control) via the control bytes XOFF (pause transmission, 0x13, Ctrl-S) and XON (resume transmission, 0x11, Ctrl-Q) is active, and in which direction; it can take the values: `SP_XONXOFF_DISABLED` (default), `SP_XONXOFF_IN`, `SP_XONXOFF_OUT`, and `SP_XONXOFF_INOUT`
