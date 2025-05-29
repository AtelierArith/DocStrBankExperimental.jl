```
open_stream(inlet::StreamInlet; timeout=LSL_FOREVER)
```

Subscribe to the data stream.

All samples pushed in at the other end from this moment onwards will be queued and eventually be delivered in response to pull*sample() or pull*chunk() calls. Pulling a sample without some preceding open_stream is permitted (the stream will then be opened implicitly).

Function may throw a timeout error, or lost error (if the stream source has been lost).

# Keyword arguments

  * `timeout::Number`: timeout of the operation.
