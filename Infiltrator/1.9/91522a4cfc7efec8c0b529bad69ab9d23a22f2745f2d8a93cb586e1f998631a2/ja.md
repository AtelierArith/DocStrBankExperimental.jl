```
@infiltry expr
```

式をtryブロックでラップし、例外が発生した場合に浸透します。これは次のものと同等です：

```julia
try
    expr
catch
    @infiltrate
    rethrow()
end
```

`expr`が`x = f(...)`の形である場合、私たちは`x`をスコープから取り出します。

```julia
x = try
    f(...)
catch
    @infiltrate
    rethrow()
end
```
