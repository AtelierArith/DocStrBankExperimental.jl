```
NxPacket(timestamp::Int,data::Matrix{Real})
```

Individual data packet (potentially multiple per file). The `timestamp` is the temporal offset of this packet (using the processor `clock_frequency`) and `data is a 2D, "time" x "channel"`Matrix`.
