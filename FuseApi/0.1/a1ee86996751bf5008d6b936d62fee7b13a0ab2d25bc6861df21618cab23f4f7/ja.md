```
FuseFileInfo <: Layout
```

多くのfuseコールバックで使用されるC構造体のレイアウト。

C構造体は`libfuse3` Cライブラリによって割り当てられ、ポインタとしてコールバック関数に引数`fi::Ptr{FuseFileInfo}`として渡され、`CStruct(fi)`変換によってJuliaにアクセス可能になります。
