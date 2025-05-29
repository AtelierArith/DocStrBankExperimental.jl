```
Mode(m::UInt8)
Mode(;user::UInt8=0o0, group::UInt8=0o0, other::UInt8=0o0)
Mode(mode::UInt8, usr_grps::Symbol...)
Mode(str)
```

Provides an abstraction for working with posix file permissions. A lot of the low level permissions code for this type was below and the corresponding constants have been translated from cpython's [Lib/stat.py](https://github.com/python/cpython/blob/master/Lib/stat.py).

# Example

```julia-repl
julia> Mode("-rwxr-x--x")
-rwxr-x--x
```
