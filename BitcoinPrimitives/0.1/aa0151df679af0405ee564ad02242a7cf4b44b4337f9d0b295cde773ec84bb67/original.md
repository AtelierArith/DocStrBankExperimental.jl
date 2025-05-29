```
check_pow(header::Header) -> Bool
```

Returns whether this header satisfies proof of work

```
get the hash256 of the serialization of this header
interpret this hash as a little-endian number
return whether this integer is less than the target
```
