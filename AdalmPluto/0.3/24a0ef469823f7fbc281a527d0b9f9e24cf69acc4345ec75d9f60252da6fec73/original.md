```
openPluto(txCfg, rxCfg[, uri, backend])
```

Creates a PlutoSDR struct and configures the radio to stream the samples.

# Arguments

  * `txCfg::ChannelCfg` : the port / bandwidth / sampling rate / carrier frequency for the tx channels.
  * `rxCfg::ChannelCfg` : the port / bandwidth / sampling rate / carrier frequency for the rx channels.
  * `bufferSize::UInt=1024*1024` : the buffer size in samples.
  * `uri::String="auto"` : the radio uri (ex : "usb:1.3.5"). "auto" takes the first uri found for the given backend.
  * `backend::Union{nothing,String}` : the backend to scan for the auto uri. If not specified, all backend are scanned and the first radio found is used.

# Returns

  * `radio::PlutoSDR` : a fully initialized PlutoSDR structure.
