```
sequence!(rp::RedPitaya, seq::AbstractSequence)
```

Transmit the client-side representation `seq` to the server and append it to the current list of sequences. Return `true` if the required commands were successful.
