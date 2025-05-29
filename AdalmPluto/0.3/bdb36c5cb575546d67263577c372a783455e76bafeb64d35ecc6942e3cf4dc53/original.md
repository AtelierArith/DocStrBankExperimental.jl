```
openPluto(carrierFreq, samplingRate, bandwidth[, uri, backend])
```

Creates a PlutoSDR struct and configures the radio to stream the samples.

# Arguments

  * `carrierFreq::Int` : the carrier frequency for both tx and rx.
  * `samplingRate::Int` : the sampling rate for both tx and rx.
  * `gain::Int` : the analog RX gain.

# Keywords

  * `addr::String="auto"` : the radio address (ex: "usb:1.3.5"). "auto" takes the first uri found for the given backend.
  * `backend::Union{nothing,String}` : the backend to scan for the auto uri. If not specified, all backend are scanned and the first radio found is used.
  * `bufferSize::UInt=1024*1024` : the buffer size in samples.
  * `bandwidth::Int` : the bandwidth for both tx and rx.

# Returns

  * `radio::PlutoSDR` : a fully initialized PlutoSDR structure.
