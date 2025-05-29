```julia
LArray(::Tuple, ::NamedTuple)
LArray(::Tuple, kwargs)
```

`LArray`の標準コンストラクタ。

例えば：

```julia
LArray((2, 2), (a = 1, b = 2, c = 3, d = 4))  # サイズを指定する必要があります
LArray((2, 2); a = 1, b = 2, c = 3, d = 4)
```
