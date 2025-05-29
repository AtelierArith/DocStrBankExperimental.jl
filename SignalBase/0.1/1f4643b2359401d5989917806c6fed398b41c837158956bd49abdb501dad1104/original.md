```
duration(x)
```

Return the duration of the signal in seconds, if known. May return `missing` (e.g. for a stream).

!!! note
    A fallback implementation of `duration` uses `nframes(x) / framerate(x)`. However, if one or both of these is `missing` and you want `duartion` to return a non-missing value, you can define a custom method of `duration`.

