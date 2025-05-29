Returns whether this block satisfies proof of work

```
get the hash256 of the serialization of this block
interpret this hash as a little-endian number
return whether this integer is less than the target
```
