```
witharray_read(f, v::CeedVector, mtype::MemType=MEM_HOST)
```

[`witharray`](@ref)と同様ですが、データへの読み取り専用アクセスを提供します。

# 例

ベクトルの内容を表示します：

```
witharray_read(display, v)
```
