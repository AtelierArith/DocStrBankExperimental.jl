```
sp_flush(port::Port, buffers::SPBuffer)
sp_flush(port::SerialPort, buffers::SPBuffer)
```

Discard data in the selected serial-port buffer(s).

Supported values for `buffers`: `SP_BUF_INPUT`, `SP_BUF_OUTPUT`, `SP_BUF_BOTH`

Returns `SP_OK` upon success or raises an `ErrorException` otherwise.

!!! note
    Not to be confused with `Base.flush`, which writes out buffered data rather than discarding it: the underlying `libserialport` C library unfortunately uses the verb “flush” differently from its normal meaning for `Base.IO` (`sp_drain` provides the latter in this library).

