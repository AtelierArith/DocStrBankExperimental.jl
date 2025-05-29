```
write_frames(file, dicts)
```

`file`に原子配置のシーケンスを書き込みます。`dicts`の代わりにChannelを渡すことで非同期に使用することもできます。例えば：

```julia
Channel() do ch
    @async write_frames(outfile, ch)

    for frame in frames
        put!(ch, frame)
    end
end
```
