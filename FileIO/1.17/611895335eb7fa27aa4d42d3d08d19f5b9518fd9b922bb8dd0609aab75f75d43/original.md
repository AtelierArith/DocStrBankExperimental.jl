```
skipmagic(s::Stream)
```

Sets the position of `s` to be just after the magic bytes. For a plain IO object, you can use `skipmagic(io, fmt)`.
