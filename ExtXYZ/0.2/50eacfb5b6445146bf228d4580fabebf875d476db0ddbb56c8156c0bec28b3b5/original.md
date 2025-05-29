```
write_frames(file, dicts)
```

Write a sequence of atomic configurations to `file`. Can also be used asynchronously by passing a Channel in place of `dicts`, e.g.

```julia
Channel() do ch
    @async write_frames(outfile, ch)

    for frame in frames
        put!(ch, frame)
    end
end
```
