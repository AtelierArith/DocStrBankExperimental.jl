```
data, S = record(time::Real = 5; input_device, args=(1,0), chat::Bool=true)
```

Record `time` seconds of audio data using `input_device` (typically defaults to the built-in microphone).

# Input

  * `time` : duration; 5 seconds by default

# Option

  * `input_device::PortAudioDevice = get_default_input_device()` system default
  * `args` : arguments to PortAudioStream; `(1,0)` for single-channel input by default
  * `chat` : show begin/end message? `true` by default

# Output

  * `data` : Vector of length `time * S`
  * `S` : `sample_rate` of input stream
