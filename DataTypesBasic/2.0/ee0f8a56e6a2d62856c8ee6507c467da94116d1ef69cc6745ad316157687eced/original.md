```
@Try begin
  your_code
end
```

Macro which directly captures an Excpetion into a proper `Try`representation.

It translates to

```julia
try
  r = your_code
  Identity(r)
catch exc
  Const(Thrown(exc, Base.catch_stack()))
end
```
