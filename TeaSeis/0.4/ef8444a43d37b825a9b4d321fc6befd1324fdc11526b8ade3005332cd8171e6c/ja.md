```
ind2sub(io, i)
```

インデックス `i` に対する (frame, volume...) タプルを返します。これは、4次元以上のデータセット内のすべてのフレームをループ処理するのに便利です。例えば、

```julia
for i = 1:length(io)
    trcs, hdrs = readframe(io, ind2sub(io,i)...)
end
```
