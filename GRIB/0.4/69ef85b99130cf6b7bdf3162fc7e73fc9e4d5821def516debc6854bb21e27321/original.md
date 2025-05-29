```
Message(raw::Vector{UInt8})
Message(messages::Vector{Vector{UInt8}})
```

Create a Message from a bytes array or array of bytes arrays.

The Message will share its underlying data with the inputed data.
