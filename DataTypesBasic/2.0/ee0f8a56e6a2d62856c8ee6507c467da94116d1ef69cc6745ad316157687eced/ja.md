```
@Try begin
  your_code
end
```

例外を適切な `Try` 表現に直接キャプチャするマクロです。

次のように変換されます。

```julia
try
  r = your_code
  Identity(r)
catch exc
  Const(Thrown(exc, Base.catch_stack()))
end
```
