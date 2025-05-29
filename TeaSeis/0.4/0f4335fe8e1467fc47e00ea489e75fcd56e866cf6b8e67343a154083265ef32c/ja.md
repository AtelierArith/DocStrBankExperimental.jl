```
fold(io, hdrs)
```

フレームのフォールドを計算します。ここで、ioはデータセットに対応するJSeisであり、hdrsはフレームのヘッダーです。例えば: `io=jsopen("file.js"); fold(io, readframehdrs(io,1))`
