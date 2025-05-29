```
@TryCatch YourException begin
  your_code
end
```

特定のエラーのみをキャッチする[`@Try`](@ref)のバージョンです。他のすべてのエラーは`rethrown`されます。

これは次のように翻訳されます。

```julia
try
  r = your_code
  Identity(r)
catch exc
  if exc isa YourException
    Const(Thrown(exc, Base.catch_stack()))
  else
    rethrow()
  end
end
```
