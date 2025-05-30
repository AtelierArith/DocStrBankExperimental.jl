```
infiltrate(mod, locals, file, line)
```

`@infiltrate`の関数形式。これを使用して、e.g. Reviseを使用せずにパッケージコードに条件付きで浸透します（このバージョンは事前コンパイル中に有効です）。

通常、次のように使用されます。

```julia
if isdefined(Main, :Infiltrator)
  Main.infiltrate(@__MODULE__, Base.@locals, @__FILE__, @__LINE__)
end
```
