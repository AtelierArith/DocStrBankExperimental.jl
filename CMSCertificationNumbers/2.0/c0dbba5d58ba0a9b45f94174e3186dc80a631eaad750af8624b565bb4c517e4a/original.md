```
sequence_number(ccn) -> Int64
```

Decode the sequence number from a given CCN.

Sequence numbers are sometimes indefinite. If this is the case, then only the decodable digits of the sequence number are returned (typically the last digits).
