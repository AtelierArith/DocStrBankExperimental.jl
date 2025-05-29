```
Mode(m::UInt8)
Mode(;user::UInt8=0o0, group::UInt8=0o0, other::UInt8=0o0)
Mode(mode::UInt8, usr_grps::Symbol...)
Mode(str)
```

posixファイル権限を扱うための抽象を提供します。このタイプの低レベルの権限コードの多くは以下にあり、対応する定数はcpythonの[Lib/stat.py](https://github.com/python/cpython/blob/master/Lib/stat.py)から翻訳されています。

# 例

```julia-repl
julia> Mode("-rwxr-x--x")
-rwxr-x--x
```
