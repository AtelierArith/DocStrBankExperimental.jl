```
readmeta(f::Function, file::AbstractString)
```

`readmeta()`のDoブロックバリアント。次のように使用します：

```
readmeta("libfoo.so") do f
    ...
end
```
