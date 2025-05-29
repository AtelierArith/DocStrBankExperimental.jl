```
can_concatenate(::Codec)::Bool
```

Return `true` if the codec has concatenation transparency.

If `true`, and some encoded data `a` and `b` decode to `x` and `y` respectively, then the concatenation of `a` and `b` will decode to the concatenation of `x` and `y`
