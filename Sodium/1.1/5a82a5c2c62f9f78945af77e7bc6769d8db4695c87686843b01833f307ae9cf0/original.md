```
seal(message::Vector{UInt8}, publickey)
```

Convenience function which wraps the message in a `SecretBuffer` before calling `seal(::SecretBuffer, publickey)`. Also wipes and empties the message vector.
