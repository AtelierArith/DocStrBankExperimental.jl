```julia
kill!(mod::Module) -> ::Nothing
```

`kill!` はアクティブな `Toolips` サーバーを停止します。

```julia
pm::Toolips.ProcessManager = start!(Toolips, "127.0.0.1":8000)
kill!(Toolips)
```

  * 参照: `route`, `start!`, `Toolips`, `new_app`
