```julia
kill!(mod::Module) -> ::Nothing
```

`kill!` will stop an active `Toolips` server.

```julia
pm::Toolips.ProcessManager = start!(Toolips, "127.0.0.1":8000)
kill!(Toolips)
```

  * See also: `route`, `start!`, `Toolips`, `new_app`
