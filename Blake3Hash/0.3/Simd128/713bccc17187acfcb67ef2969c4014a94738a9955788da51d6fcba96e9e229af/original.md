```
update!(self::Blake3Ctx, input::AbstractVector{UInt8}, datalen=length(input))::Nothing
```

Hash more data.  This method can be called multiple times until all the data has been hashed.
