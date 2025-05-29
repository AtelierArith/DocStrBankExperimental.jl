```
NoPad()
NoPad(border)
```

Indicates that no padding should be applied to the input array, or that you have already pre-padded the input image. Passing a `border` object allows you to preserve "memory" of a border choice; it can be retrieved by indexing with `[]`.

# Example

The commands

```
np = NoPad(Pad(:replicate))
imfilter!(out, img, kernel, np)
```

run filtering directly, skipping any padding steps.  Every entry of `out` must be computable using in-bounds operations on `img` and `kernel`.
