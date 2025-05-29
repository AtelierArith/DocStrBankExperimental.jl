```
VirtualOffset(block_offset::Integer, inblock_offset::Integer)
```

Create a virtual file offset from `block_offset` and `inblock_offset`. Get the two offsets with `offsets(v)`.

`block_offset` is an offset pointing to the beginning position of a BGZF block in a BGZF file and `inblock_offset` is an offset pointing to the begining position of a binary data within a uncompressed BGZF block. These values are zero-based and their valid ranges are [0, 1 << 48) and [0, 1 << 16), respectively.
