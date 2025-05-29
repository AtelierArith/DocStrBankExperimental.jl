```
octave(T, [n=1])
```

Returns the interval corresponding to an octave for interval type `T`. For interval classes, this should return `zero(T)` (a default method is provided).

If `n` is specified, the octave is multiplied by `n` first. This is equivalent to `octave(T) * n`.

For convenience, a fallback for `octave(p::T, [n])` is provided. Only `octave(T)` needs to be implemented.
