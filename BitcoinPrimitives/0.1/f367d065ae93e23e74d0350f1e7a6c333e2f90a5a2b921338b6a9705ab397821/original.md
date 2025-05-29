```
Header
```

Data Structure representing the Header of a Block in the Bitcoin blockchain.

Data are store as an `NTuple{80, UInt8}` without parsinf per se. The elements of the `Header` can be accessed by `header.element`.

```julia
header.version
header.prevhash
header.merkleroot
header.time
header.bits
header.nonce
```
