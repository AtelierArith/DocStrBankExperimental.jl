```
get_library_name(filename::AbstractString)
```

OS依存のライブラリ名を返します 

# 例

```
get_library_name("mylibrary")
```

  * Windows: `mylibrary.dll`
  * MacOS: `libmylibrary.dylib`
  * Linux: `libmylibrary.so`
