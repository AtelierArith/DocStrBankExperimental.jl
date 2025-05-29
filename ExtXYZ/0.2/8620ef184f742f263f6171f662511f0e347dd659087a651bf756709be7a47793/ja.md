```
iread_frames(file[, range])
```

ExtXYZファイルから読み取るためのChannelを返します。フレームは1つずつ生成されます。`range`は単一の整数、範囲オブジェクト、またはフレームインデックスの整数配列であることができます。

使用例:

```julia
ch = iread_frames("file.xyz")
for frame in ch
    process(frame)
end
```
